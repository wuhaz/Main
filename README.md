# Main
All My Main Scripts

<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Clipboard copy examples</title>
    <script type="module" src="https://unpkg.com/@github/clipboard-copy-element@latest"></script>
    <!-- <script type="module" src="../dist/index.js"></script> -->
    <style>
      clipboard-copy {
        -webkit-appearance: button;
        -moz-appearance: button;
        padding: 0.4em 0.6em;
        font: 0.9rem system-ui, sans-serif;
        display: inline-block;
        cursor: default;
        color: rgb(36, 41, 47);
        background: rgb(246, 248, 250);
        border-radius: 6px;
        border: 1px solid rgba(31, 35, 40, 0.15);
        box-shadow: rgba(31, 35, 40, 0.04) 0 1px 0 0, rgba(255, 255, 255, 0.25) 0 1 0 0 inset;
      }
      clipboard-copy:hover {
        background: rgb(243, 244, 246);
      }
      clipboard-copy:active {
        background: #ebecf0;
      }
      clipboard-copy:focus-visible {
        outline: 2px solid #0969da;
      }
      .textarea {
        margin-top: 30px;
        display: block;
      }
    </style>
    <script>
      document.addEventListener('clipboard-copy', function (event) {
        const notice = event.target.querySelector('.notice')
        announce.setAttribute('aria-label', 'Copied');
        notice.hidden = false
        setTimeout(function () {
          announce.setAttribute('aria-label', '');
          notice.hidden = true
        }, 1000)
      })
    </script>
  </head>
  <body>
    <main aria-labelledby="h">
      <h1 id="h">Demo</h1>
      <div aria-live="polite" id="announce"></div>
      <section>
        <p>Copy from <code>value</code> attribute:</p>
        <clipboard-copy value="@hubot copied from [value]">
          Copy
          <span class="notice" hidden>Copied!</span>
        </clipboard-copy>
      </section>
      <hr />

      <section>
        <p>Copy from an element specified by the <code>for</code> attribute:</p>
        <div id="name">@hubot copied from &lt;div&gt;</div>
        <clipboard-copy for="name">
          Copy
          <span class="notice" hidden>Copied!</span>
        </clipboard-copy>
      </section>
      <hr />

      <section>
        <label>
          <p>Copy from an input element specified by the <code>for</code> attribute:</p>
          <input id="login" value="@hubot copied from &lt;input&gt;" size="40" />
        </label><br />
        <clipboard-copy for="login">
          Copy
          <span class="notice" hidden>Copied!</span>
        </clipboard-copy>
        </section>
      <hr />

      <section>
        <label>
          Paste the text here to test
          <textarea class="textarea" rows="10" cols="50"></textarea>
        </label>
      </section>
  </body>
</html>
