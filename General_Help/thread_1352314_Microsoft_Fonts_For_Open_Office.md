---
title: "Microsoft Fonts For Open Office"
date: 2009-12-11
forum: General Help
---

### Post by loweehahn on 2009-12-11
I've noticed that Microsoft fonts have been removed from Open Office Writer after I've upgraded to 9.10 and I can't reinstall the fonts from the software centre. Has anyone of you encountered this problem too and how can I reinstall the fonts? And what happens when Microsoft Word can't recognize a particular font?

---

### Post by PaulReaver on 2009-12-11
copy your windows fonts into /home/yourname/.fonts/

as long as you have a microsoft license on the machine its legal to have them in ubuntu.

---

### Post by emigrant on 2009-12-11
i think its available in the restricted extras as well:
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Uncle Spellbinder on 2009-12-11
1. Go to terminal (Application > Accessories > Terminal) and type:

    ```
sudo apt-get install msttcorefonts
```

2. Refresh the fonts cache, to do so type:

    ```
sudo fc-cache -fv
```

---

### Post by BobSongs on 2009-12-11
"DNS Resolve" seems much slower in Karmic. This is a known problem (that's why some websites seem to take an unusually long time to load).

The fix that worked for me (and repeated installs of **ttf-mscorefonts-installer** didn't work) is commented in bugs.launchpad.net by "Laurent". Here's the link and I'll quote the text for the readers.

The text Laurent removed is in bold red text.

Link: [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217/comments/21](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217/comments/21)

> To me it seems a pb of DNS time out.
 I solved the [problem] with this workaround/dirty patch.
 In the file **/var/lib/****dpkg/info/****ttf-mscorefonts****-installer.****postinst** (coming with package first install),
I removed the DNS time out in watchdog  line 148 to get

 > if ! wget --continue --tries=1 [COLOR=Black]--connect-timeout=5 [/COLOR]--read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

  instead of

 > if ! wget --continue --tries=1 [COLOR=Green]**[COLOR=Red]--dns-timeout=10[/COLOR] **[COLOR=Black]--connect-timeout=5[/COLOR][/COLOR] --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

 But I can not tell you why it failed with this package and not with others.
So, essentially, remove **[COLOR=Red]--dns-timeout=10[/COLOR]** from the text and your fonts will download (tested personally).

---

### Post by joes7 on 2009-12-11
Download your desired fonts. Put them on the System's "fonts" folder. This should work, and will apply the recently installed fonts to every program that allows one to change font.

---

### Post by loweehahn on 2010-01-25
I got Microsoft Office fonts in my Open Office now. Thanks for your help.

---

### Post by Greekbiggles on 2010-09-27
Many thanks, Uncle Spellbinder.  Now to install some Greek ones....

---

