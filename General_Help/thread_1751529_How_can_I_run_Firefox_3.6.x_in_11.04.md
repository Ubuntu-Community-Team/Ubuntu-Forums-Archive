---
title: "How can I run Firefox 3.6.x in 11.04?"
date: 2011-05-06
forum: General Help
---

### Post by steffi on 2011-05-06
With the upgrade to 11.04 from 10.10 I notice that Lotus inotes no longer works. possibly because of the big jump to Firefox 4 from 3.

How can I have Firefox 3.6.x and Firefox 4 both installed?

when I try to run Firefox 3.6.x from the command line it launches
Firefox 4

---

### Post by Finalfantasykid on 2011-05-06
You can't have both running at the same time.  If you have Firefox4 open, close all it's windows and open firefox 3.6

---

### Post by Frogs Hair on 2011-05-06
I have had Two different Firefox versions installed in the past . one regular and a development release . I don't see why you could not do it . I have not installed Firefox from the website , so I won't be any help with that . I should add that I did not have both open at once. [http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)

---

### Post by Frogs Hair on 2011-05-06
Sorry ,

I some how missed that you had 3.6 installed already . I'm not sure why there would be a conflict because they separate applications just as Minefield and Firefox 3.6 were in my case . When I installed 11.04 I had FF 4 and FF 6 Nightly Alpha 1 installed at the same time until I removed FF 4 to install Opera.

---

### Post by lovinglinux on 2011-05-07
If you have both already installed, then you need to use a different user profile and the -no-remote option to start 3.6 when Firefox 4 is already running.

If you don't have Firefox 3.6 already installed, then see the manual installation method of [http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)

---

### Post by steffi on 2011-05-07
I didn't say I want to run both at the same time. I just want more than one version to coexist in the OS so I can run 3.6.x because 11.04 comes with 4.0

> **Finalfantasykid said:**
> You can't have both running at the same time.  If you have Firefox4 open, close all it's windows and open firefox 3.6

---

### Post by gourky on 2011-05-26
Hello,

first I have to mention, that I'm still a newbie in Linux, though I already tried out several Linux distributions. But I always gave up and returned to my old OS. Now Ubuntu works really fine and I'm very happy with that ;)

Since I need an older Version of Firefox because of an add-on which is not available for ff4, I tried to install firefox 3. I followed this instruction ([http://www.wikihow.com/Install-multiple-versions-of-Firefox-on-Ubuntu](http://www.wikihow.com/Install-multiple-versions-of-Firefox-on-Ubuntu)) and put the older version into another folder and extracted it there. 
After that I created two profiles but whichever profile a choose it always opens firefox 4. If I open firefox 3 manually and close it afterwards both profiles now open firefox 3.  I just don't understand how this profile-manager is working.

I don't need both versions at the same time so maybe there's a workaround so a don't need that profile-manager? A shortcut would do as well but creating a link didn't work. :(

Ah, well and I got an error after I opened this firefox I'm now typing in.
I opened it by :  
~/firefox3$ firefox no-remote -P

(firefox-bin:3856): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
[GLX] your GL driver is currently blocked. If you would like to bypass this, define the MOZ_GLX_IGNORE_BLACKLIST environment variable.


Since I do not want to work with windows forever I have to go through this somehow. I hope you'll understand my problem though my English is far from acceptable.

many greetings

---

### Post by lovinglinux on 2011-05-26
> **gourky said:**
> Since I need an older Version of Firefox because of an add-on which is not available for ff4...

Which add-on?

---

### Post by gourky on 2011-05-26
Hi,

I'm currently working with XForms and the easiest way to display the form is using firefox. There are still other possibilities but with firefox it worked just fine.

---

### Post by lovinglinux on 2011-05-26
> **gourky said:**
> Hi,

I'm currently working with XForms and the easiest way to display the form is using firefox. There are still other possibilities but with firefox it worked just fine.

You could try to install it in Firefox 4 by disabling compatibility check. You can do that with [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/").

However, I wouldn't get too much dependent on an extension that hasn't been updated for an year. The authors should have updated it by now, if they have any intentions of keeping this extension alive. 

Keep in mind that Mozilla has started a new aggressive development schedule. Firefox 5 is already beta, Firefox 6 and Firefox 7 are already under development. 

I don't know when Mozilla will stop supporting Firefox 3.6, but I guess it shouldn't be far away. So, downgrading your Firefox is just delaying the inevitable. If the authors do not update the extension, it will simply become abandonware sooner or later.

---

### Post by gourky on 2011-05-27
Thanks for your help. I installed [Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). Unfortunately Mozilla XForms is not working with ff4. I'll open ff3 by going to the folder where it is installed. 
But with your words in mind I'm also looking for another solution so I don't have to use ff anymore.

Thanks so much.

---

### Post by lovinglinux on 2011-05-27
> **gourky said:**
> Thanks for your help. I installed [Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). Unfortunately Mozilla XForms is not working with ff4. I'll open ff3 by going to the folder where it is installed. 
But with your words in mind I'm also looking for another solution so I don't have to use ff anymore.

Thanks so much.

You are welcome.

I hope you find a solution.

---

