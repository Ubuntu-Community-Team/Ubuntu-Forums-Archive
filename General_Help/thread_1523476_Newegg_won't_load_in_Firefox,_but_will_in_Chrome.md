---
title: "Newegg won't load in Firefox, but will in Chrome"
date: 2010-07-03
forum: General Help
---

### Post by river226 on 2010-07-03
So this is a bazaar problem and i haven't the slightest idea what's wrong... newegg won't load in firefox, and hasn't in a while, even though i have done plenty on newegg in firefox, but when i go on chrome it loads like there isn't the slightest problem.
Firefox is my main browser so i want to surf newegg in FF and not Chrome, so can anyone help me?

---

### Post by SmokeyThePanda on 2010-07-03
Hmm..If you mean [http://www.newegg.com]("http://www.newegg.com/") , it just loaded on my firefox. It could possibly be that your firefox is out of date? What exactly occurs when you visit the site?

---

### Post by Windows Nerd on 2010-07-03
> **river226 said:**
> So this is a bazaar problem and i haven't the slightest idea what's wrong... newegg won't load in firefox, and hasn't in a while, even though i have done plenty on newegg in firefox, but when i go on chrome it loads like there isn't the slightest problem.
Firefox is my main browser so i want to surf newegg in FF and not Chrome, so can anyone help me?
I am assuming CLI knowledge below:

Maybe launch firefox from the CLI and then give us some error messages?

```
firefox
```

Does Firefox crash when you open Newegg or what does it tell you exactly the problem is?

Could you also tell us what version of Firefox you are using? 

```
firefox --version
```

Scott

---

### Post by SmokeyThePanda on 2010-07-03
Also, just as a note, you could run firefox in safe mode and see if it happens to be one of your plugins you have installed..Once you have it opened in safe mode, you would simply turn on plugins as you browse until one of them messes it up again..

You could do this one of two ways. You could right click your firefox icon and go to properties. Then add *-safe-mode* to the command, just behind *firefox*.

The second method, which is a bit easier, would be to open your terminal and run[I]:

firefox -safe-mode[/I]

---

### Post by lovinglinux on 2010-07-04
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

---

### Post by river226 on 2010-07-04
Thanks, the Safe-mode path worked, when i reset the defaults it worked

---

### Post by bsoder on 2010-07-04
I am going to assume that no troubleshooting has been done at this point just in case anything was missed, it will be covered.

[LIST=1]
[*]Try clearing Cache and Cookies in Firefox and restart the browser.  Do this by going: Tools, Clear recent history, and select everything.  Make sure Cache and Cookies are checked.
[*]See if Firefox is connecting to a proxy server that may be conflicting with something on newegg.  Edit, Preferences, Click Advanced, click on Configure how Firefox connects to the Internet, and see if there is a custom proxy server set up.
[*]As people have said before, go to the Terminal and press firefox -safe-mode.  Try connecting and if this works, the problem may be an add-on.  Try removing add-ons that were recently installed and see if that fixes the problem.
[/LIST]

Also, what exactly is happening when you try to go to newegg.com?  Is it just stuck in loading the page?  Does it return you to an error page?

Also when did this start happening?  Did it just randomly happen after you did no changes to your computer?  Are there any other sites that you are having this problem with in Firefox, or is it just newegg?

---

### Post by bsoder on 2010-07-04
Sorry left the edit window open too long and didn't realize it was already solved.

---

### Post by pheonix7117 on 2010-12-26
A less-invasive (possible) fix at: [http://support.mozilla.com/ak/questions/762363](http://support.mozilla.com/ak/questions/762363)

Essentially, it says:
> Try:

   1. Navigating to about:config
   2. Searching for "intl.accept_languages"
   3. Right click on the matching result and click "Reset". 

Newegg doesn't respond if you send a malformed Accept-Language header. There is some plugin that is changing the default value for that header (I'm pretty sure it is, or was, Firefox Sync)


---

### Post by topdownjimmy on 2011-01-02
> **pheonix7117 said:**
> A less-invasive (possible) fix at: [http://support.mozilla.com/ak/questions/762363](http://support.mozilla.com/ak/questions/762363)

Essentially, it says:
> Try:

1. Navigating to about:config
2. Searching for "intl.accept_languages"
3. Right click on the matching result and click "Reset".

Newegg doesn't respond if you send a malformed Accept-Language header. There is some plugin that is changing the default value for that header (I'm pretty sure it is, or was, Firefox Sync) 

Thanks, that did it for me.

---

