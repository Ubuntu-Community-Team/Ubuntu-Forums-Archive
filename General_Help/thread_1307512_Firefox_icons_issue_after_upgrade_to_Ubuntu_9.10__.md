---
title: "Firefox icons issue after upgrade to Ubuntu 9.10 / FF 3.5"
date: 2009-10-31
forum: General Help
---

### Post by Irishpolyglot on 2009-10-31
Hi all!
Glad to report that this time the upgrade went much smoother for me than the 9.04 one. I only have minor issues and this is one of them: Firefox 3.5.4 is having trouble displaying icons and this is affecting how I can use some plugins.

The search bar on the right has all of the search sites I had saved, but none of them are showing their icons when I click the drop down list. It will show it when selected however.

Google Toolbar is completely chopped down and only showing one or two icons - the search bar and all the other parts have gone. I've gone into the toolbar's icons but playing around in there hasn't helped.

What this has mostly affected is certain plugins like Read-It-Later, which require the icon on a toolbar. Now it is completely unaccessible graphically (only works through shortcuts).

I've tried disabling all plugins to see if one was causing this, but the right search bar's icons still aren't displaying.
Thanks for any help on this! I really hope to solve it; I'd hate to have to downgrade Firefox.

---

### Post by lovinglinux on 2009-10-31
Close Firefox, then go to "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus".

---

### Post by Irishpolyglot on 2009-10-31
Excellent! That has fixed the first half of the problem, and the Applications, Places, System are showing the icons too. I find it strange that this option is disabled by default...

I can see the icons in the side search, but I am still having the Google Toolbar issue. Also, before the upgrade when I right clicked any (non Google) toolbar and selected "Customise..." there were way more icons that I could drag into the toolbar than there are now. All the icons were related to my plugins, but now they are just the default and Google related.

Finally, I'm having an annoying error. After I look at the "Customise..." window and close it, the close doesn't seem to be registered and Firefox is still not displaying other toolbars and the File, Edit, View etc. cannot be clicked and I have to restart the 'fox.

Thanks again for any tips!

---

### Post by tobiasly on 2009-10-31
> **lovinglinux said:**
> Close Firefox, then go to "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus".

Thanks for the info. I wonder why on earth is this not the default setting? It was very frustrating that none of my menus in the entire system had icons; I'm a long time Ubuntu user and never would have thought to look there!

---

### Post by hsmak_linux on 2009-10-31
> **lovinglinux said:**
> Close Firefox, then go to "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus".

Very kool! I have one of my problems solved by this!

---

### Post by randyklein99 on 2009-10-31
> **Irishpolyglot said:**
> Excellent! That has fixed the first half of the problem, and the Applications, Places, System are showing the icons too. I find it strange that this option is disabled by default...

I can see the icons in the side search, but I am still having the Google Toolbar issue. Also, before the upgrade when I right clicked any (non Google) toolbar and selected "Customise..." there were way more icons that I could drag into the toolbar than there are now. All the icons were related to my plugins, but now they are just the default and Google related.

Finally, I'm having an annoying error. After I look at the "Customise..." window and close it, the close doesn't seem to be registered and Firefox is still not displaying other toolbars and the File, Edit, View etc. cannot be clicked and I have to restart the 'fox.

Thanks again for any tips!

Sounds like I have a similar problem.  My firefox toolbars (google and lastpass) are fine with the first instance of Firefox being opened.  But if I open any more instances, both those toolbars are missing.  I just upgraded to 9.10 today.  I did not have this problem with 9.04.  BTW, I'm running FF 3.5.2.

---

### Post by randyklein99 on 2009-10-31
> **randyklein99 said:**
> Sounds like I have a similar problem.  My firefox toolbars (google and lastpass) are fine with the first instance of Firefox being opened.  But if I open any more instances, both those toolbars are missing.  I just upgraded to 9.10 today.  I did not have this problem with 9.04.  BTW, I'm running FF 3.5.2.

Ok, seems like some of my problem got fixed by disabling the "Ubuntu Firefox Modifications 0.8" add-on.

---

### Post by Irishpolyglot on 2009-10-31
I thought I had already disabled all plugins, but disabling just that one did the trick!
Now let me ask you something: when you right click and select "Customise..." and then close the customise window, are extra toolbars disabled (as they are during the Customise customisation) and the File, Edit etc. unclickable? I suppose this isn't that big a deal since I rarely customise the toolbar, but it's still a messy error that requires a restart.

---

### Post by vukasin0 on 2009-11-02
Hi,

After upgrade from 9.04 x86_64 to 9.10 x86_64, I've lost my firefox at all -- it crashed during start.

Here is output from CLI when try to start:

```

ubuntu:~/Desktop$ firefox
Segmentation fault (core dumped)

```


This is from /var/log/messages
```

Nov  2 15:43:05 vukasin-t60 kernel: [29716.527336] firefox[950]: segfault at ffffffffa0762560 ip 00007f059c500679 sp 00007fff833c8d50 error 4 in libgobject-2.0.so.0.2200.0[7f059c4f1000+44000]
Nov  2 15:43:05 vukasin-t60 kernel: [29823.512112] firefox[1789]: segfault at ffffffff8ee62560 ip 00007f2c8ac00679 sp 00007fff0b151fd0 error 4 in libgobject-2.0.so.0.2200.0[7f2c8abf1000+44000]
Nov  2 15:43:05 vukasin-t60 kernel: [29838.638795] firefox[1906]: segfault at 51362560 ip 00007fcd4d100679 sp 00007fff55351b60 error 4 in libgobject-2.0.so.0.2200.0[7fcd4d0f1000+44000]
Nov  2 15:43:08 vukasin-t60 kernel: [29848.596587] firefox[1973]: segfault at 46162560 ip 00007fc541f00679 sp 00007fff295d61d0 error 4 in libgobject-2.0.so.0.2200.0[7fc541ef1000+44000]

```


Same happen to my friend - he updated his Kubuntu.

Seems that I have problem with "libgobject-2.0.so"

BTW - I've downloaded firefox from mozilla's site and it is working like a charm but without flash and java support.

Any idea - solution?

Thx,
Vukasin

---

### Post by Irishpolyglot on 2009-11-02
You should start a new thread for that - it has nothing to do with the issue I was discussing.
After another reboot, the problem has gone entirely and my Google toolbar is working fine.

---

### Post by ncmncm on 2009-11-04
> 
Close Firefox, then go to "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus".


Brilliant! Thank you!
Ha! Search, patience and a solution works! Everytime! 

Please tag this thread with as many words as possible. 


A migration to KK somehow creates icon issues for many people. 
They need to come here!

---

### Post by alien-377h on 2009-11-20
> **randyklein99 said:**
> Ok, seems like some of my problem got fixed by disabling the "Ubuntu Firefox Modifications 0.8" add-on.

This worked for me. Thanks

---

