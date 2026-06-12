---
title: "Firefox temporarily freezes"
date: 2012-03-10
forum: General Help
---

### Post by lalawawa on 2012-03-10
I was on 10.04, and I ran into a problem where when I loaded a new page, firefox would freeze, usually for about 30 seconds, then it would wake up and be fine.

I thought it might be some form of Linux virus.  I don't know how I would have caught a virus, the only way binary executables get to my Linux box is through the synaptic package manager, or a build them from source myself.

It was bad enough that I installed epiphany and started using it.  I don't like epiphany as much as firefox, but it wasn't freezing.  Then after a few days, it began to freeze like firefox did.

I uninstalled and reinstalled firefox.  The problem seemed to get better for awhile, then it came back after a few days.  I concluded that the virus had infected other binaries on my system, and eventually was able to reinfect firefox.

I installed 11.04 from DVD (I had been on 10.04), wiping my disk clean.  When I installed software from backup, I made sure to delete and rebuild from source all my own binary executables.

So now I'm on a whole new release, and firefox is still freezing the same way.  The firefox is version 10.0.2, I don't remember what it was when I was on 10.04.

---

### Post by winh8r on 2012-03-10
Some tips for firefox


use the following add-ons:

ad-block plus

ghostery

Also click on the link "Help with Flash" in my sig below and install Flash Aid and run the wizard to correctly configure your flash version and plugins.

If firefox is still sluggish, this sometimes helps too:

open firefox

click on the + symbol (new tab)

enter the following:

```
about:config
```

accept the warning and continue.


enter this into the search box:

```
ipv6
```


when you see the line that says

```
network.dns.disableIPv6
```

right click on it and select "Toggle"

the word "false" should now read "true"

close the tab and restart firefox.


Hope this helps

---

### Post by Topsiho on 2012-03-10
What is that: a virus? As far as I know there are no viruses for Linux (in the wild). So you don't have a virus.

What can happen is that by installing software from source, you did possibly install (yourself) some application that is malware, or contains malware, and you did that yourself. (a virus needs to install itself, but can't, as it doesn't know your password).

Then there are other possibilities, lack of resources, for instance. Possibly you have a slow diskdrive, so that when used heavily, the processor has to wait. Or the processor has to wait for the contents of the working memory (RAM) to be swapped first, before it can continue. Then you have not enough RAM.

Topsiho

---

### Post by lalawawa on 2012-03-10
winh8r, your solution completely worked.  I surfed around for an hour or two to be sure, but the probelm seems to be completely gone!

Thank you so much.  I never could have figured that out myself.

---

### Post by winh8r on 2012-03-10
Glad to hear you got it sorted out.


Happy surfing.

---

### Post by lalawawa on 2012-03-17
I had another problem that resulted in my having to reinstall 11.04 from scratch.  This time I did the same trick to the firefox config, but now, after restarting firefox and even rebooting, the firefox temporary freeze problem has come back.

---

### Post by lalawawa on 2012-03-18
When I start firefox, it says "failed to create drawtable".

When if freezes, it says

/usr/lib/firefox-11.0/plugin-container: /usr/lib/libssl3.so: version `NSS_3.13.2' not found (required by /usr/lib/firefox-11.0/libxul.so)
/usr/lib/firefox-11.0/plugin-container: /usr/lib/libnss3.so: version `NSS_3.12.10' not found (required by /usr/lib/firefox-11.0/libxul.so)

So I went to the Synaptic Package Manager and installed everything with "NSS" in its name, then restarted firefox, but the exact same problem persists.

---

