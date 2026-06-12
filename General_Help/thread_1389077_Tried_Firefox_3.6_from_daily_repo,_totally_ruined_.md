---
title: "Tried Firefox 3.6 from daily repo, totally ruined font rendering on entire sys"
date: 2010-01-23
forum: General Help
---

### Post by Malakai on 2010-01-23
So yeah. I used the directions from this thread:

[http://ubuntuforums.org/showthread.php?t=1352580](http://ubuntuforums.org/showthread.php?t=1352580)

Then after installing it, I realized not only did firefoxes fonts look terrible, the fonts on the entire system were totally different, they look terrible.

So I uninstalled all the new programs, removed the new moz repository, and then reinstalled the regular firefox 3.5 from regular ubuntu repos. Dropped all support software down to 3.5 as well. System fonts are still totally fubar!

I tried creating a .fontconfig file with the text from the threads, supposedly to fix the new firefoxes fonts, and it did not help.

Need help, as my fonts looked absolutely wonderful, now they look terrible. I tried messing with all the settings in the appearance tab of the gnome menu, nothing seems to help!

Thanks in advance for the help. Regular firefox is back, and running fine, but its fonts and all the rest of the fonts on the system look horrible, like they are not getting aliased/hinted at all!

---

### Post by kerry_s on 2010-01-24
did you log out & back in?

---

### Post by lidex on 2010-01-24
Run these commands in a terminal, one line at a time.

```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig 
sudo fc-cache -f -v
```

"Applications>Accessories>Terminal"

---

### Post by nanotube on 2010-01-24
did you try going to system->preferences->appearance->fonts, and play with those settings?

---

### Post by jmszr on 2010-01-24
I installed Namoroka 3.6 from this PPA:  [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) . Now all fonts are a little bit "off" but quite usable except that the Ubuntu Forums font has changed to what appears to be the Sawasdee font (okay if that's what you like) but I use Arial.

I went to System > Preferences > Appearance > Fonts, but nothing I did there changed much of anything.

I've run lidex's commands - the first one didn't take - "no such file or directory", but the next two went through with no change to the fonts.

If anyone can shed some light on this it would be much appreciated - I can live with Sawasdee until 10.04, but I do find it rather irritating.

Thanks

---

### Post by lovinglinux on 2010-01-24
> **jmszr said:**
> I installed Namoroka 3.6 from this PPA:  [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) . Now all fonts are a little bit "off" but quite usable except that the Ubuntu Forums font has changed to what appears to be the Sawasdee font (okay if that's what you like) but I use Arial.

I went to System > Preferences > Appearance > Fonts, but nothing I did there changed much of anything.

I've run lidex's commands - the first one didn't take - "no such file or directory", but the next two went through with no change to the fonts.

If anyone can shed some light on this it would be much appreciated - I can live with Sawasdee until 10.04, but I do find it rather irritating.

Thanks

You could try **Solution** [*[COLOR="Red"]**FOT012**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT012). That might help, but it doesn't work for most people with similar problems due to this update.

---

### Post by jmszr on 2010-01-24
lovinglinux,

Thanks, but it was a no go. I'll either just live with it or perhaps try Swiftweasel.

By the way - Thank you for UMarks, it is a very useful add-on.

---

### Post by lovinglinux on 2010-01-24
> **jmszr said:**
> lovinglinux,

Thanks, but it was a no go. I'll either just live with it or perhaps try Swiftweasel.

By the way - Thank you for UMarks, it is a very useful add-on.

You are welcome and thanks for downloading UMarks.

---

### Post by inigo48 on 2010-01-24
i have the font problem too. and the [FOT012] solution from the Troubleshooting guide wasn't useful.

any other idea? 

i think it would be a great feature in ubuntu if you could upgrade some popular applications more easily (firefox, thunderbird, openoffice). now the safe way is to use the outdated app until the next ubuntu version.

---

### Post by lidex on 2010-01-25
I don't have that .font.config file on my system and I don't have that problem. I initially had the fuzzy fonts when I updated to 3.5 and fixed it with the commands I posted previously. Perhaps removing that file and refreshing the font cache will help.

---

### Post by Malakai on 2010-01-25
> **nanotube said:**
> did you try going to system->preferences->appearance->fonts, and play with those settings?

> **kerry_s said:**
> did you log out & back in?


Believe me, I am not a noob, I would not have started a thread if it was something simple. No rudeness intended =)


My partition scheme was fubar from the initial install, I did not intend to be keeping this install, it was all installed on sda7/8 with a bunch of different partitions.

So I just went ahead and reinstalled ubuntu. Needless to say I will not be trying to install firefox 3.6 that way again =)

Should this happen again I will try the advise of some of the other posters. Thanks for the help =) A reinstall fixed it, obviously =)

---

### Post by Terry Zhou on 2010-01-25
I have the same problem and tried this way [http://carlo-hamalainen.net/blog/?p=291](http://carlo-hamalainen.net/blog/?p=291), it's better, but still not the same as system fonts.

---

### Post by ironjaw33 on 2010-01-28
I'm having font rendering issues as well.  I'm running 9.10 64 bit and the fonts look great in Firefox 3.5.  However, installing 3.6 from the daily builds and also from the Mozilla download page, the fonts look blurry. 

I've tried messing with the .fonts.conf file as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1200992&page=3"), which also affects the rendering in Firefox 3.5, VLC, and Skype, but I can tweak the file so it looks good.  However, the same .fonts.conf settings don't help Firefox 3.6.

I've also tried the same methods as the above poster and, as he said, it's better, but not quite as good as the system fonts.

Any other ideas?

---

### Post by chandru on 2010-01-28
I have posted a possible fix in this thread. Hope this helps.

[http://ubuntuforums.org/showpost.php?p=8739169&postcount=31]("http://ubuntuforums.org/showpost.php?p=8739169&postcount=31")

---

