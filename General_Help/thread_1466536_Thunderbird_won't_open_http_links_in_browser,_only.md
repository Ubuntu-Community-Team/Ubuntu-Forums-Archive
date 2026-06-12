---
title: "Thunderbird won't open http links in browser, only https"
date: 2010-04-30
forum: General Help
---

### Post by mrowth on 2010-04-30
When I click on an http link in Thunderbird, nothing at all happens. There's no error message on the console, there's no new browser starting, and there's no new tab opening with the browser already running. 

I've tried: sudo update-alternatives --config x-www-browser, choosing firefox.

I've also tried: adding a new string value to Thunderbird's warranty-voiding config: network.protocol-handler.app.http, with a value of /usr/bin/firefox. This was recommended in various threads.

But no luck.

There's an entry for https - firefox on the Attachment tab of the preferences, and https links are indeed opening in Firefox. But not http.

I would welcome any help.

KDE 4.4.2 itself has default mail client and browser set to Thunderbird 3.0.4 and Firefox 3.6.3 (both from the repositories, no website downloads).

---

### Post by mrowth on 2010-04-30
Anyone?

---

### Post by GandG on 2010-05-01
Believe the 'missing' Http entry in Thunderbird's Attachments preferences might be reinstated through editing your mimeTypes.rdf file. The significance being that it then may allow Firefox to open your failing Http links.

1. Shut TB 

2. Backup/rename mimeTypes.rdf in TB profile 

3. Edit/ create new  mimeTypes.rdf to include Http entries

Mine looks like shown below (there's an "en-GB entry" which might need changing) ; -           

```

<?xml version="1.0"?>
<RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <RDF:Description RDF:about="urn:scheme:https"
                   NC:value="https">
    <NC:handlerProp RDF:resource="urn:scheme:handler:https"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:schemes">
    <NC:Protocol-Schemes RDF:resource="urn:schemes:root"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:http"
                   NC:value="http">
    <NC:handlerProp RDF:resource="urn:scheme:handler:http"/>
  </RDF:Description>
  <RDF:Seq RDF:about="urn:schemes:root">
    <RDF:li RDF:resource="urn:scheme:https"/>
    <RDF:li RDF:resource="urn:scheme:http"/>
  </RDF:Seq>
  <RDF:Description RDF:about="urn:root"
                   NC:en-GB_defaultHandlersVersion="-1" />
  <RDF:Seq RDF:about="urn:mimetypes:root">
  </RDF:Seq>
  <RDF:Description RDF:about="urn:scheme:handler:https"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false" />
  <RDF:Description RDF:about="urn:scheme:handler:http"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false" />
  <RDF:Description RDF:about="urn:mimetypes">
    <NC:MIME-types RDF:resource="urn:mimetypes:root"/>
  </RDF:Description>
</RDF:RDF>

```


4. Restart TB - check whether Http is now in Attachment Preferences

5. If so, change Http action to "Always Ask"

6. Restart TB?

7. Open a previously failing E-mail Http link - hopefully a dialogue should then ask if you want to use Firefox for such links - permanently, if required.

---

### Post by mrowth on 2010-05-01
Amazing help, thank you!

---

