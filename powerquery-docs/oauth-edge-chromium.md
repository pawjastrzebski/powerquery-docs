---
title: Enabling Microsoft Edge (Chromium) for OAuth authentication in Power BI Desktop
description: This article describes how users can install and use Microsoft Edge (Chromium) for OAuth authentication in Power BI Desktop. 
author: DougKlopfenstein
ms.service: powerquery
ms.reviewer: dougklo
ms.date: 8/31/2021
ms.author: dougklo
---

# Enabling Microsoft Edge (Chromium) for OAuth authentication in Power BI Desktop

If you're using OAuth authentication to connect to your data, the OAuth dialog in Power Query uses the Microsoft Internet Explorer 11 embedded control browser. However, certain web services, such as QuickBooks Online, Salesforce Reports, and Salesforce Objects, no longer support Internet Explorer 11.

As of December of 2020, Power BI Desktop now uses [Microsoft Edge WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/) for OAuth authentication with certain connectors. These connectors are:

* GitHub
* QuickBooks Online
* Salesforce Reports
* Salesforce Objects
* Smartsheet
* Twilio
* Zendesk

On your Power BI Desktop machine, you can get WebView2 control either by installing the new Edge (Chromium) browser (at least beta) from [https://www.microsoftedgeinsider.com/download](https://www.microsoftedgeinsider.com/download), or by installing the [WebView2 redist package](https://developer.microsoft.com/microsoft-edge/webview2/#download-section).

All other connectors will use Internet Explorer 11 by default unless the settings are overridden using environment variables.

* To enable WebView2 for all connectors, set `PQ_EdgeChromiumOAuthAllowListAll` to true:

   ```
   setx PQ_EdgeChromiumOAuthAllowListAll   true
   ```

* To enable WebView2 for specific connectors, set `PQ_ExtendEdgeChromiumOAuthAllowList` with the name(s) of the connector(s) you want to enable. Multiple connectors are separated by semicolons.

   ```
   setx PQ_ExtendEdgeChromiumOAuthAllowList   MyExtension1;MyExtension2
   ```

* To disable the use of WebView2, set `PQ_DisableEdgeChromiumOAuth` to true.

   ```
   setx PQ_DisableEdgeChromiumOAuth   true
   ```
