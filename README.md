// Function to dynamically add a script to the document head
function addScriptToHead(src) {
    const script = document.createElement('script');
    script.src = src;
    document.head.appendChild(script);
}

// Function to dynamically add a stylesheet to the document head
function addStylesheetToHead(href) {
    const link = document.createElement('link');
    link.rel = 'stylesheet';
    link.href = href;
    document.head.appendChild(link);
}

// Function to fetch URLs from environment variables or Secrets Manager
function getUrlsFromSecretsOrEnv() {
    // Fetch URLs from environment variables or Secrets Manager
    const script1Url = process.env.SCRIPT1_URL || 'default_script1_url';
    const script2Url = process.env.SCRIPT2_URL || 'default_script2_url';
    const cssUrl = process.env.CSS_URL || 'default_css_url';

    return { script1Url, script2Url, cssUrl };
}

// Fetch URLs and add scripts and stylesheet to the head
async function addScriptsAndStylesToHead() {
    try {
        // Retrieve URLs
        const { script1Url, script2Url, cssUrl } = getUrlsFromSecretsOrEnv();

        // Add scripts and stylesheet to the head
        addScriptToHead(script1Url);
        addScriptToHead(script2Url);
        addStylesheetToHead(cssUrl);
    } catch (error) {
        console.error("Error fetching URLs:", error);
    }
}

// Call the function to add scripts and stylesheet to the head
addScriptsAndStylesToHead();
