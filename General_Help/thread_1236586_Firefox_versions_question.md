---
title: "Firefox versions question"
date: 2009-08-10
forum: General Help
---

### Post by KarenAK on 2009-08-10
During the transition to Firefox 3.6 I have been able to use 2 Firefox versions on my comp - Minefield and the consecutive Ff versions up to Shiretoko now. 

With yesterday's update however, most of my add-ons that worked ok in Minefield up to now, are disabled. 

Since the simultaneous use of 2 independent Firefox versions is perfect for some of the stuff I do, I now need advice on how to either downgrade Minefield or how to run two independent Shiretoko instances. (It's not good enough to just open another Firefox window !) 

Can someone help me with this, please ?

Thanks in advance :-)

---

### Post by lovinglinux on 2009-08-10
> **KarenAK said:**
> With yesterday's update however, most of my add-ons that worked ok in Minefield up to now, are disabled.

You can disable extension compatibility check. See the Extension Compatibility section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

I use 43 extensions and none of them are giving me trouble, even with the compatibility disabled. The thing is that unless they need code re-writing (sometimes they do), the compatibility is just a matter of declaring the version of Firefox the extension will work, in the installation file. So, disabling the compatibility check allow them to work even if they haven't been tested with the new FF version.

Nevertheless, some extensions I use do not work at all with FF 3.6a1 (Namoroka), but I believe you are using 3.5 not 3.6 as stated, since Shiretoko is 3.5.

Either way, you should try to update your extensions first, by clicking "Find updates" in the add-ons dialog.

> **KarenAK said:**
> Since the simultaneous use of 2 independent Firefox versions is perfect for some of the stuff I do, I now need advice on how to either downgrade Minefield or how to run two independent Shiretoko instances. (It's not good enough to just open another Firefox window !) 

I guess what you need is two different profiles, not two different versions. For coincidence, Shiretoko makes a copy of your profiles from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5, so any changes while using Shiretoko does not affect FF 3.0 settings.

To launch Firefox with a different profile, not just another window run this code in a terminal:

```
firefox -P -no-remote
```

Then select a profile to use or create a new one.

Additional information on the tutorial mentioned above.

---

### Post by KarenAK on 2009-08-10
Ok, the disabling of the compatibility check didn't work but the profiles did.

I had no idea that one could run 2 profiles simultaneously. PERFECT :-)


Now, two last noob questions:

1.) How can I copy the bookmarks / settings / addons etc. from one profile to the other ? Do I simply copy the contents of the one folder into the other ?

2.) Is there a way to launch this 2nd profile from the panel instead of in the terminal window and if so - how ?


Thank you very much for your help :-)

---

### Post by KarenAK on 2009-08-10
oh, btw - About Minefield says that it's version 3.6a2pre

---

### Post by lovinglinux on 2009-08-10
> **KarenAK said:**
> 
1.) How can I copy the bookmarks / settings / addons etc. from one profile to the other ? Do I simply copy the contents of the one folder into the other ?

Yes.

> **KarenAK said:**
> 2.) Is there a way to launch this 2nd profile from the panel instead of in the terminal window and if so - how ?

Create a launcher in the panel and set the command to:

```
firefox -no-remote -P "profilename"
```

Where profilename is the actual profile name you see in the Profile Manager, not the folder name. Don't remove the quotes, they are necessary.

---

### Post by KarenAK on 2009-08-11
This works perfectly. 

Thank you very much :-)

---

