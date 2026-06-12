---
title: "Problems importing Thunderbird information from Ubuntu 11.10 to 12.04"
date: 2012-05-04
forum: General Help
---

### Post by neorich2002 on 2012-05-04
Today I took the plunge, wiped my system and installed the new 12.04 Ubuntu. It's lovely except for one issue.

Before wiping my old system I backed up the .thunderbird folders hoping to simple use it with the new Thunderbird to get all my accounts and mail etc. When I try to use this folder though, and open Thunderbird it crashes after about 10 seconds.

I can run Thunderbird fine without this folder.

Does anyone have any ideas what's going on here?

Thanks

neorich2002

---

### Post by papibe on 2012-05-04
Hi neorich2002.

Try launching it from the terminal to see if it display more error messages:
```
thunderbird
```
My first guess would be there's a permissions problem. Could you post the result of this command?
```
ls -la .thunderbird/
```
Regards.

---

### Post by neorich2002 on 2012-05-04
Thanks papibe for your suggestions. 

I have run

```
thunderbird
```

in the terminal and there were no error reports or any output at all. When thunderbird crashes it offers to send a report to the developers.

The output of:

```
ls -la .thunderbird
```

was:

```
total 20
drwx------  4 neorich2002 neorich2002 4096 May  4 20:39 .
drwxr-xr-x 35 neorich2002 neorich2002 4096 May  4 20:37 ..
drwx------  4 neorich2002 neorich2002 4096 May  4 20:39 Crash Reports
-rw-------  1 neorich2002 neorich2002   94 May  4 20:39 profiles.ini
drwx------ 15 neorich2002 neorich2002 4096 May  4 20:39 s040x7zg.default

```

Thanks

Regards

neorich2002

---

### Post by skutter2k on 2012-05-29
I have exactly the same problem. I presume this is a new version of thunderbird so the folder is not going to work :-(  Has anyone sorted a workaround for this?  I need to access my emails!

---

### Post by habana on 2012-05-30
Just for your information, I performed a new installation of 64 bit 12.04 and copied over all the hidden files from my 32 bit 11.10 installation. Thunderbird (and most everything else) works perfectly with all my old data and preferences.

---

### Post by colin.p on 2012-05-30
I have Thunderbird set to IMAP for my Gmail account (since Intrepid), so all my messages are still on the server. However, I have kept all my saved POP messages from before I went to IMAP in a separate folder called "local folders" that have been saved since 1998 or so. Every upgrade, I install Thunderbird, set up my mail, then copy over my "mail" folder overwriting the new "mail" folder. Then all saved messages are there. I could just copy over the "local folders" as well but I have always done it this way.

One thing I should note, that I started with Intrepid then upgraded every new release until Lucid. After two years on Lucid, I forgot how to re-configure the OS and it took a little head scratching and alot of searching to get it just right. I will be a physical wreck after 5 years on Precise.

---

### Post by timgood on 2012-05-30
I have also successfully imported all my emails from 11.10 into 12.04 so I don't think it's anything to do with updates. Are you running any add-ons? Try disabling all the add-ons, or renaming the add-on folder and then start Thunderbird again. You can always re-install the add-ons if this works.

Hope this might help.

---

### Post by jvdurme on 2012-07-04
I have the same issue as the thread starter. When my old profile folder is present in the new .thunderbird folder, it crashes.
Hence I have no access to my 5000+ mails, euhmm... darn.

Anyone? Permissions are ok.

I come from Maverick to Precise. Thunderbird profiles should be the same I guess.

PS: this did the trick:

> thunderbird -safe-mode

---

### Post by haresear on 2012-07-04
I've used an older profile folder to import into 12.04 thunderbird. One thing to check is that the name of the default folder in the 'profiles.ini' file matches the name of the default folder in '.thunderbird'.

---

