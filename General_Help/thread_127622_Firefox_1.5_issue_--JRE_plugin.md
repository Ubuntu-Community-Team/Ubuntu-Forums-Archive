---
title: "Firefox 1.5 issue --JRE plugin"
date: 2006-02-09
forum: General Help
---

### Post by Prospero2006 on 2006-02-09
This is strange:

   I have two instances of Firefox installed:
          -1 is the default adept 1.0.7 install
          -1 is the latest package offered through 
            Firefox. (I have a link to the binary on the desktop)

   Now,  whenever I encounter a java applet with the 
   1.5 install, the non-default package, it doesn't recognize
   that I've installed JRE1.5. (Missing Plugin Error)

    However, when I open the same page with 1.0.7, 
    it runs the applet just fine.

           -What's up with that?
                  -Thanks,
                       Prospero

---

### Post by flight_master on 2006-02-09
Hi,

When you install a new instance of FireFox, you will also need to install the plugs for it again. I'm not sure if this won't cause conflicts though, as it is never a good idea to run two versions of the same program simultaneously. I'd still suggest to go ahead and re-install JRE, it may fix your problem ;)

-Christian

---

### Post by Prospero2006 on 2006-02-09
Much appreciated. 
I found a solution in case this may be helpful to folks in the future.

I unpacked the current firefox-*.tar.gz in /downloads/firefox
I linked it to my desktop.
I then did:

ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /downloads/firefox/plugins/

That did the trick. It's gotta have it in the specific plugin directory. 


Pros

---

