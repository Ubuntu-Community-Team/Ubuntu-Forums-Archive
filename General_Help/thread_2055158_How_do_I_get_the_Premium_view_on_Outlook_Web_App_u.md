---
title: "How do I get the Premium view on Outlook Web App using Chrome on Linux?"
date: 2012-09-08
forum: General Help
---

### Post by HunterDX77M on 2012-09-08
The Outlook Web App (OWA) has two versions: Premium and Light. Premium is the default, but if it's unable to be supported, it goes to the Light version which is a stripped down version with no effects or dynamic behavior.

Premium works automatically on almost all browser/OS combinations except for the specific one I am using: Chrome on Linux. You cannot switch to Premium while using Chrome on Linux. I heard there was an extension or workaround that could "trick" OWA into thinking that Chrome on Linux was a compatible browser. Does anyone know of it?

---

### Post by HunterDX77M on 2012-09-11
Bumpity bump

---

### Post by dcstar on 2012-09-12
> **HunterDX77M said:**
> The Outlook Web App (OWA) has two versions: Premium and Light. Premium is the default, but if it's unable to be supported, it goes to the Light version which is a stripped down version with no effects or dynamic behavior.

Premium works automatically on almost all browser/OS combinations except for the specific one I am using: Chrome on Linux. You cannot switch to Premium while using Chrome on Linux. I heard there was an extension or workaround that could "trick" OWA into thinking that Chrome on Linux was a compatible browser. Does anyone know of it?

There is no "trick". "Premium" uses proprietary IE functions (like ActiveX) that other standards compliant browsers do not have.

"Light" uses features common to all browsers (like JavaScript) and is not as functional because Microsoft deliberately design their systems to only work with 100% functionality with other MS products.

---

### Post by HunterDX77M on 2012-09-13
> **dcstar said:**
> There is no "trick". "Premium" uses proprietary IE functions (like ActiveX) that other standards compliant browsers do not have.

"Light" uses features common to all browsers (like JavaScript) and is not as functional because Microsoft deliberately design their systems to only work with 100% functionality with other MS products.

But then how does it explain why the Premium version works fine in Firefox (all OS's), Safari and Chrome (on non-Linux OS's)?

Secondly, I saw someone running Ubuntu and viewing the Premium version on Chrome. When I asked them about it, they specifically told me it was with an extension that "tricked" Outlook into thinking Chrome worked.

---

### Post by thedrewsk on 2012-09-14
> **HunterDX77M said:**
> But then how does it explain why the Premium version works fine in Firefox (all OS's), Safari and Chrome (on non-Linux OS's)?

Secondly, I saw someone running Ubuntu and viewing the Premium version on Chrome. When I asked them about it, they specifically told me it was with an extension that "tricked" Outlook into thinking Chrome worked.

Pretty sure that dcstar is right seeing as I just checked our OWA on Firefox and Chrome (Windows 7 x64) and they are both forced to light mode.

Not sure if this is what you're looking for but you may find some helpful info at this link [http://weblog.etherized.com/posts/183]("http://weblog.etherized.com/posts/183")

---

### Post by HunterDX77M on 2012-12-22
For anyone wondering about this still, I found a solution that involves tricking OWA into thinking you have a different user agent. Run the following from the terminal and you should be able to use the premium OWA.

```
/opt/google/chrome/google-chrome --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/6.0.481.0 Safari/534.4"
```

---

### Post by psypher on 2013-01-10
Nice, works like a charm. What limitation does this have on other websites?

Now just to get Fogger and Ubuntu WebApp Integration to work!

---

### Post by dcstar on 2013-01-10
> **psypher said:**
> Nice, works like a charm.
...........

Really?, do **all** the Premium Outlook Web features work?

The main reason MS do not allow Premium for non-IE browsers is because they provide things that **only** work with IE.

You might fool the server into delivering the Premium code, but if it contains stuff like ActiveX then I doubt everything will work outside of IE.

---

### Post by psypher on 2013-01-10
Looks to me everything is working. At least what I need for now, Mail, Calendar, Rules, GAL lookups. Is there any specific Premium feature you want me to test? I haven't used it much in the past so not sure what's premium and whats not. I just know it looks way better, faster and more like Outlook.

---

### Post by pentastich on 2013-02-13
Hi David,

I thought that Outlook Web required IE specific features also, but I can verify that the full feature set is available for Firefox on Linux.  According to Microsoft, Chrome v18 is also supported on Linux.  See the following link for more information: [http://office.microsoft.com/en-us/support/supported-browsers-for-outlook-web-app-HA102824601.aspx](http://office.microsoft.com/en-us/support/supported-browsers-for-outlook-web-app-HA102824601.aspx)

-- Jim

---

### Post by chedlin on 2013-05-29
> **thedrewsk said:**
> Pretty sure that dcstar is right seeing as I just checked our OWA on Firefox and Chrome (Windows 7 x64) and they are both forced to light mode.

Not sure if this is what you're looking for but you may find some helpful info at this link [http://weblog.etherized.com/posts/183]("http://weblog.etherized.com/posts/183")

That was the case with 2007.  Outlook 2010 now supports more.  But the fact that Chrome on Linux isn't supported without UA faking really irks me.

---

### Post by col.panic on 2013-07-08
Yeah I would look into an addon that can do per site user agent string stuff, so that it only changes your user agent string for Outlook Web App.  Search the chrome web store for "User-Agent Switcher for Chrome"

To give more background if someone stumbles across this on google as I did.  There is some confusion in this thread as I believe that some of the posters have experiences based on different versions of OWA.  Most people are most familiar with Outlook Web Access that was available in Exchange 2003.  It was actually pretty good as long as you used IE.  It was garbage with everything else.  In this version of OWA the premium view used vbscript and activeX stuff to do all of the handy "premium" features.  Even if you spoofed your user agent string, the site did not even come close to looking like it worked.  Ironically, OWA 2003 works pretty terribly in IE 10, in my experience.

I don't have any experience with OWA 2007, but I do use OWA 2010 all the time.  I believe in 2007 they started down the road towards, I'll call it, "more web standards based design" for OWA.  This is what allows them to let you use the premium view in any of the 4 major browsers.  It is no longer an actual technical limitation that causes them to limit their support, but a support limitation.  Still... It totally blows that they do not allow you to override the "Lite View" without doing UA string hacks.

---

### Post by dcstar on 2013-07-08
> **col.panic said:**
> Yeah I would look into an addon that can do per site user agent string stuff, so that it only changes your user agent string for Outlook Web App.  Search the chrome web store for "User-Agent Switcher for Chrome"
..........

I support OWA professionally, if people not using IE can get things like the Appointments pop-up to function (just like it does in "real" Outlook) then they can claim to have full functionality, until then the thing is still deliberately limited to IE for **full** functionality.

---

### Post by lowebb on 2013-07-18
Logged in especially.  HunterDX77M's, superb works great. Thanks v. much!

---

### Post by exohuman on 2013-08-14
I use the User Agent Spoofer and have it set to only spoof for the Outlook Web App. I gave a custom user agent:

name: Chrome Windows
string: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/28.0.1500.95 Safari/537.36
flag: CW

Works perfectly! It appears that Outlook Web App does *not* depend on IE. It wants you to use Windows...

---

### Post by ossifragus on 2013-08-23
Could you give more details how this has been done? Thank you.

---

### Post by rick-ucker on 2013-09-19
Ossifragus, I just fixed my issue using the [User Agent Switcher]("https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg?hl=en-US") addon for Chrome. After installing the addon I clicked its button in the Chrome UI and chose Settings. From there I added a new agent string using the values posted by exohuman above. After I did that I activated that switched to the tab where I had my email open, activated the new user agent string. At this point the tab reloaded. I think I had to sign out and back in again to see the full Office 365 UI instead of the "Lite" version.

---

