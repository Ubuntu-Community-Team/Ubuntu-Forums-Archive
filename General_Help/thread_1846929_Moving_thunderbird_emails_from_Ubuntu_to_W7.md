---
title: "Moving thunderbird emails from Ubuntu to W7"
date: 2011-09-19
forum: General Help
---

### Post by roobydoo on 2011-09-19
Already spent 1/2hr googling this with NO simple answer.

I have a copy of my complete Ubuntu .thunderbird email profile folder for my POP email account. I copied the folder onto a backup hard drive and plugged it into my W7 machine. How do I get W7 Tbird to recognize the new profile and read it?

My linux box needs to come offline as it's on the fritz. But I can get it running enough to re-save the file or do something in Linux first before I back it up again.

So far any help I have found is Win -> Ubuntu, not Ubuntu -> Win oriented. Plus it's jargon heavy and not very concise (and this from someone who was coding at age 6). Somebody really needs to write a decent tutorial on this.

Edit - running Tbird 3 and Ubuntu 10.4 - profile editing offline

    Shane

---

### Post by roobydoo on 2011-09-19
Did find a solution.
 
This tutorial [http://ubuntuforums.org/showthread.php?t=1701190&highlight=thunderbird+dual-boot](http://ubuntuforums.org/showthread.php?t=1701190&highlight=thunderbird+dual-boot) while not quite the same produced exactly the results I was looking for.

To clarify - I was looking in appdata/local where there is in fact a folder for thunderbird, but it's the appdata/roaming folder that allows you to find the file named profiles you need. 

Make sure, if you have copied the **.mozilla-thunderbird** folder into your W7 **appdata/roaming/thunderbird** folder, that in the **profiles** file you change the location from **/profiles/(random char).default** to **/.mozilla-thunderbird/(random char).default** using notepad

If it's within the SAME thunderbird folder, the changing of the line **defaultisrelative=0** to** =1 **is not as important as if you are looking for a folder somwhere outside of the thunderbird folder - IE: another drive as dicussed in the tutorial.

---

