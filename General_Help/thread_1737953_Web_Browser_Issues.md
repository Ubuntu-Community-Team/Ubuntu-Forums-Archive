---
title: "Web Browser Issues"
date: 2011-04-24
forum: General Help
---

### Post by Broadlighter on 2011-04-24
Hi This is my first time here ):P

I have an issue with my web browsing. I installed Ubuntu 10.10 on a Dell Machine.

FireFox 3.6.16 came with the Ubuntu installation.

FireFox boots up. I get the home page. I am able to navigate to some websites without trouble. When I visit sites with richer content, that's where I run into trouble. When I go to Yahoo.com, Yahoo's main page appears with scrambled text and no images. I click on the mail link and the mail page loads just fine.

After logging into Yahoo mail, getting to the mail list page or opening a listed e-mail is hit or miss. When I click on a link in the message body of an e-mail that is hit or miss.

When I go to Facebook and try clicking on a link that someone posted to my wall, Firefox gets hosed and it never leaves that page or starts up another tab in Firefox. Videos don't play, either. It's usually the 2nd or 3rd link after the login page where things stop working.

To test and troubleshoot this further, I downloaded Chromium 10.0.648.133(77742) using Ubuntus Synaptic Package Manager. The Application downloaded and installed without issue. However, I got the same behavior in Chromium as I did in Firefox.

The Internet doesn't seem to be a problem. I can use the Synaptic Package Manager and other apps that use the Internet. The problem has to be with the web browsers, Ubuntu or the combination of the two.

Would someone please help and give some ideas of why this would be happening and how to fix it, if possible.

Thanks,

John H.

---

### Post by dino99 on 2011-04-24
you need to install some extra packages from synaptic:

- check the repo tab: enable canonical partner repo, then update
- install flasplugin-installer
- install ubuntu-restricted-extras

---

### Post by Broadlighter on 2011-04-25
Didn't see anything in the Synaptic Package Manager that had to do with a Repo tab. There was one Canonical item in the list, but it didn't resemble "Canonical Partner Repo."

I'm currently downloading and applying the Flash Plugin Installer and Ubuntu Restricted Extras. I'll let you know how it goes. In the meantime, if you have any more information about Canonical Partner Repo and how to find it, let me know.

Thanks,

---

### Post by Broadlighter on 2011-04-25
Followed your instructions without the Canonical Partner Repo update and still having the same problems. Any help with updating Canonical Partner Repo would be greatly appreciated.

Thanks,

Broadlighter

---

### Post by lovinglinux on 2011-04-25
To update the repos all you need is to run sudo apt-get update.

Anyway, I recommend that you use my Flash-Aid extension:

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by lithopsian on 2011-04-25
This is nothing to do with Flash or with Ubuntu extras, both of which can cause problems of their own.  At worst, missing flash will cause some panels to be missing on web pages.  In any case Chrome comes with its own Flash plugin that is pretty reliable.

Install Firefox 4.0.  See the sticky post at the top of the pages for instructions on adding the right repo, or download it direct from mozilla.org.  I don't think it will help, but you want to do it anyway :)

It sounds like you have serious networking problems.  I'm not sure where to start diagnosing these.  Does the Package Manager work well for you?

---

### Post by Broadlighter on 2011-04-25
> **lithopsian said:**
> It sounds like you have serious networking problems.  I'm not sure where to start diagnosing these.  Does the Package Manager work well for you?

I've thought as much. However, the Synaptic Package Manager and Update Manager seem to have no problem downloading apps and updates. The browsers, both FireFox and Chromium, can open certain pages. YouTube seems to work. The problems occur with extremely rich content sites like Facebook and Yahoo. 

Have not encountered any problems with local apps, either.

If there are network problems, I would like to check those, too.

---

### Post by Broadlighter on 2011-05-10
Okay, I've narrowed the problem down to the router. FireFox and Chromium are not the problem. I took the computer to a friends home and tried it out on their network which was a DSL modem/router combo and it worked fine - very fast. I came home and tried it out on the DSL modem and it sizzled.

The router is a Dynex DX-E402 4 Port 10/100 Mbps Router. I logged into the Router configuration tool, but I have no idea what to look for or change. The quick setup says everything is hunky-dory, but there must be someting else. 

I anyone has any ideas, I'm all ears.

Thanks,

Bliter

---

### Post by lovinglinux on 2011-05-11
> **Broadlighter said:**
> Okay, I've narrowed the problem down to the router. FireFox and Chromium are not the problem. I took the computer to a friends home and tried it out on their network which was a DSL modem/router combo and it worked fine - very fast. I came home and tried it out on the DSL modem and it sizzled.

The router is a Dynex DX-E402 4 Port 10/100 Mbps Router. I logged into the Router configuration tool, but I have no idea what to look for or change. The quick setup says everything is hunky-dory, but there must be someting else. 

I anyone has any ideas, I'm all ears.

Thanks,

Bliter

What is the MTU value?

---

