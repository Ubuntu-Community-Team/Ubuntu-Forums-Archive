---
title: "Firefox starts on boot - how do I stop this"
date: 2010-03-17
forum: General Help
---

### Post by charonred on 2010-03-17
Just over the past few days Firefox 3.5.8 now starts as soon as the desktop has loaded - it's not set to do this in 'Startup Applications' - how do I stop it starting on boot?

Also, over the same period, if I click a javascript link, nothing happens, it no longer opens the relevant page or image; so I click it again and still nothing, however several minutes later the page/image may open, but not always.

Also if I close Firefox, then later click a link in an email it no longer opens Firefox - I then have to go into 'System Monitor > Processes', find and then 'end process' for Firefox (cause it's sleeping) before I can actually start it.

I've gone in Synaptic and 'reinstalled' Firefox, but it made no difference. I cleared the cache and all cookies as well - could something have got into Firefox, and if so how can I fix it ?

I'm using karmic 9.10 32 bit with kernel 2.6.31-20-generic-pae

update - it appears it's a javascript problem within Firefox as I can no longer open the popup window for online banking from my banks webpage link - I can do this in other browsers such as Epiphany, Google Chrome and Opera, but not in Firefox

---

### Post by byStanderone on 2010-03-17
...perhaps you are correct, java may have something to do with your problem. had read some threads bout it, tho had forgotten bout the specifics. there are unresolved issues of java in karmic...don't know if uninstall/re-install of all java progs and firefox would correct your system.

---

### Post by charonred on 2010-03-17
bump

---

### Post by charonred on 2010-03-18
I thought Firefox's profile had become corrupt, so I deleted the profile.ini file and Firefox then created a new profile, so I've just spent the past hour installing my 'add-ons' and revisiting my various pages and saving passwords again - what a hassle ...

But the javascript problem is still there as is FF auto running when I boot ???

---

### Post by john newbuntu on 2010-03-18
Firefox loads probably because the last configuration is being remembered by the desktop manager.  First close firefox completely and kill all instances of it.  Go to system->preferences->startup apps->options. Now click the "remember currently running application".  I hope that fixes that problem.

Now, as far as the javascript problem or profile problem goes, save/export your bookmarks if any first.  Close firefox.  Then move the .mozilla folder out of the way from your home directory.  "mv ~/.mozilla ~/.moz.old"
Then open firefox again.  Do the basic setup part and see if it solves your problems.  If it does not, uninstall firefox and reinstall it.  Then lather-rinse-and repeat the last part of moving .mozilla folder out.  See if that helps.

---

### Post by lovinglinux on 2010-03-18
See the [COLOR="Sienna"]**troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by charonred on 2010-03-18
Thanks John Newbuntu
solution for Firefox starting worked a treat

your solution for javascript also worked but I ended up doing it several times; finally figuredout the cause of problem - was the 'Kallout' search Add-on that was messing the javascript

I progressively installed various Add-ons I use, but after installing 'Kallout' it went wrong again, so uninstalled it and things are fine ... shame cause I've been using that Add-on for a couple of years and never had problems with it before ... still I can live without it.

Taken the whole day to sort this out, from early this morning till dusk ...

---

