<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>QuickBooks OAuth Callback</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    pre { background: #f3f3f3; padding: 10px; border-radius: 5px; }
    .code { color: green; font-weight: bold; }
  </style>
</head>
<body>
  <h2>QuickBooks OAuth Callback</h2>
  <p>Below is the authorization code and state returned by QuickBooks:</p >
  <pre id="output"></pre>

  <script>
    function getQueryParams() {
      const params = {};
      const queryString = window.location.search.substring(1);
      const pairs = queryString.split("&");
      for (const pair of pairs) {
        const [key, value] = pair.split("=");
        params[decodeURIComponent(key)] = decodeURIComponent(value || "");
      }
      return params;
    }

    const params = getQueryParams();
    const output = document.getElementById("output");
    if (params.code) {
      output.innerHTML = `Authorization Code: <span class="code">${params.code}</span>\n\nState: ${params.state || 'N/A'}`;
    } else {
      output.innerText = "No authorization code found in the URL.";
    }
  </script>
</body>
</html>
