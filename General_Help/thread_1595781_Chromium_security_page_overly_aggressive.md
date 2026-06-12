---
title: "Chromium security page overly aggressive"
date: 2010-10-13
forum: General Help
---

### Post by d5xtgr on 2010-10-13
Thanks for viewing this thread!  I posted this a few days ago in the Security forum and got no answer; I'm posting here hoping that more traffic will lead to a better response.

I connect to the internet through a password-protected network which stores my login for one day (basically every morning I get a redirect to a website that prompts for a username and password). The problem is that since my homepage is also 'https://' I get chromium's 'This is probably not the webpage you are looking for!' message.
Quite simply, I want chromium to trust the login site enough that it will simply proceed to it without confirmation without applying this reduced security to other sites. How do I achieve this behaviour?
I spent a while looking for a solution and came up with this: [http://code.google.com/p/chromium/wiki/LinuxCertManagement](http://code.google.com/p/chromium/wiki/LinuxCertManagement)
I have difficulty understanding how I can apply this to fix my problem.

---

### Post by 3Miro on 2010-10-13
I have not dabbled in SSL so I don't even know if this page applies to your problem. However, I can give you another suggestion. Many pages on the internet are very picky about the browser that you use, so while I use chromium as my main browser, I always keep multiple browsers around (usually firefox and midori), just in case. Basically, you can try to do this with FireFox, I have used FF for this type of login before and I have had no trouble (then again maybe my system was different form yours).

I know this probably not the solution that you wanted, but it is the best I come come up with.

---

### Post by d5xtgr on 2010-10-14
Thanks!

As I understand it, the problem isn't with the website not liking Chromium- once I'm at the login page it goes fine.
Chromium has a feature that stops the page from loading and warns you whenever you try to access a secure page (beginning in [https://)](https://)) and you end up on a different page, which helps to avoid lookalike pages that steal passwords if you mistype a URL.  I want to selectively disable this feature so that the browser doesn't keep trying to protect me from my network login page.
I appreciate the suggestion, but booting into firefox to login and then changing back for general use is probably as much of a hassle as dealing with the protection thing- I currently just type google.com into my address bar; since it isn't secure, Chromium doesn't harass me.
As an alternative, can I write a script that logs into a secure webpage when I turn on the computer?

---

