---
title: "Unity Theming Panel"
date: 2011-04-28
forum: General Help
---

### Post by techunit on 2011-04-28
Hey guys I want to use the Orta theme with Ubuntu Unity however the dark panel doesn't seem to work. Can anyone help with this? I can't seem to get it working correctly.

Thanks alot,

---

### Post by davim on 2011-04-29
Same problem here :(

---

### Post by KegHead on 2011-04-29
Hi!

system...preferences...preferred applications..accessibility.

KegHead

---

### Post by techunit on 2011-04-30
That doesn't help only confuses. So any other recomendations?

---

### Post by Krytarik on 2011-04-30
> **techunit said:**
> Hey guys I want to use the Orta theme with Ubuntu Unity however the dark panel doesn't seem to work.
What specifically 'doesn't work'? Could you please post a screenshot of how it looks in Unity and Classic?

Check if the default Ambiance theme works at your install in Unity.
And if so, compare the panel specs of both.

---

### Post by techunit on 2011-04-30
> **Krytarik said:**
> What specifically 'doesn't work'? Could you please post a screenshot of how it looks in Unity and Classic?

Check if the default Ambiance theme works at your install in Unity.
And if so, compare the panel specs of both.
Thanks for the interest.

I could post an image but first I'll try to give a better description of the problem.

Theming works with all the default themes and third party themes as well other than orta with dark panel.

Orta with white panel looks and works fine.

Orta with dark panel doesn't seem to render properly and is instead replaced with what seams like either a flat white panel or the orta white panel.

The error only appears in Unity in classic ubuntu the problem doesn't exist.

I have tryed setting Orta as the theme in classic with the dark panel and switching to Unity with no luck.

It isn't an issue of hardware either I am running more than ample hardware and close to over kill in terms of memory. I am of course running 64bit.

Hopefull I don't scare anyone hoping to help off. Which is what generally happens when I have a problem. Thanks.

---

### Post by Krytarik on 2011-04-30
> **techunit said:**
> 
Hopefull I don't scare anyone hoping to help off. Which is what generally happens when I have a problem.
Hey, I'm still here, right?! Didn't I help you the last time also?! ;-)

So, it's like I said before, if you compare the both panel specifications of 'Orta /w dark panel' and '/w white panel', you should be able to pinpoint the culprit. Of course, there are some differencies regarding the text colors, but the culprit should be the settings regarding the implemention of the panel background image. You may post the respective files if you need help in that.

---

### Post by techunit on 2011-04-30
Thanks I'll see what I can do. I'll check back in a few minutes. As for scaring people off. I was refering to people who might have some knowlege but don't take the time to look into the problem. You obviously aren't one of those people.

---

### Post by ceduardo.melo on 2011-04-30
Hi! I did some changes in the original "gtk-2.0/Styles/Panel/panel-dark-default.rc". Now my "dark" panel is really dark with white text.

Replace the original with the attached in this reply, change the theme, change it back and you should have a dark panel.

---

### Post by techunit on 2011-05-01
> **ceduardo.melo said:**
> Hi! I did some changes in the original "gtk-2.0/Styles/Panel/panel-dark-default.rc". Now my "dark" panel is really dark with white text.

Replace the original with the attached in this reply, change the theme, change it back and you should have a dark panel.
Awesome thanks a ton! Please contact the auther with the fix so he/she can resolve the issue for good.

[http://gnome-look.org/messages/?action=newmessage&username=SkiesOfAzel](http://gnome-look.org/messages/?action=newmessage&username=SkiesOfAzel)

Use your gmail email to log-in in the Open-ID feild.

---

### Post by behzadsh on 2011-05-03
replacing attachment doesn't worked for me :(
Still having white panel

---

### Post by HX_unbanned on 2011-05-04
Same issue here.

ALSO, I suppose the 4x - 6x prompts for root password when Orta settings are Saved also is bug. There should be only one prompt for root password, right?

PLEEAASSEEE FIX THESE ISSUES, Devs! ;)

Launchpad Bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/777155](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/777155)

Otherwise - Orta definitely is theme that should be recommended for new Unity users.

---

### Post by luvgirl12345 on 2011-05-04
Thanks for the dark panel ;) btw i also noticed the 6 password prompts ;) I don't think thats normal ;) 

How did you guys get unity to have orta button whens maximized? If I use the fix on other site: copy, add the correct unity buttons and rename as Ambiance then the Orta settings manager seems to not recognize the theme and resets all my settings etc...

---

### Post by SkiesOfAzel on 2011-05-04
Thanks for your interest in my theme boys and girls :). I understand your frustration with the bugs but unfortunately, i don't have time to fix them at the moment. I was planning to rewrite the theme completely, reducing pixmaps and adding some murrine engine in there as well, but lack of time and the futility of it forced me to abandon the plan. Orta is a gtk2 theme and with the coming of gtk3 it will become obsolete as gtk2 themes don't work with gtk3: In 6 months time every major distro will be using gtk3.

  Please, don't take my answer as a sign of indifference, every dev that tries to contribute something free and open does it in his/hers free time, but sometimes free time is in no supply unfortunately. I might manage to upload a fix for the unity dark panel issue, but i can't promise anything.

---

### Post by mrsomoasun on 2011-06-01
The available zipped rc fix worked great.

Thanks all.

Btw, running Orta config using sudo/gksudo works around the multi-password issue.

---

### Post by morsedl on 2011-10-01
The Orta Settings Manager does not check the umask before installing files, either, so take notice if you have changed your umask setting to something other than the default of 022.

I use a umask of 077 so my files, by default, can only be read and written by me.  This setting, though, causes the settings.rc file that the Orta setting manager installs to also be written with a umask 077, which then no one can read but the root user:

morse@s3 ~> ls -lt /usr/share/themes/Orta/gtk-2.0/
total 108
-rw-------  1 root root  680 2011-10-01 21:22 settings.rc
-rw-------  1 root root  680 2011-10-01 21:21 ~settings.rc
drwxr-xr-x  2 root root 4096 2011-10-01 21:08 Lines
drwxr-xr-x  3 root root 4096 2011-10-01 21:08 Notebook_smooth
drwxr-xr-x  2 root root 4096 2011-10-01 21:08 Shadows
...

Running

  sudo chmod 644 /usr/share/themes/Orta/gtk-2.0/settings.rc

will fix the problem.

](*,)](*,)](*,)](*,)

---

