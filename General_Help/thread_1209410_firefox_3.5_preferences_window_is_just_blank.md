---
title: "firefox 3.5 preferences window is just blank"
date: 2009-07-10
forum: General Help
---

### Post by jithin1987 on 2009-07-10
Hi,
My firefox 3.5 preferences window is just blank. Please help.

Though there is no problem with firefox 3.0.10 preferences.

---

### Post by jithin1987 on 2009-07-10
Also its not saving passwords anymore. Though it keeps asking to save.

---

### Post by nikhilk on 2009-07-10
See if creating a new profile helps.
Backup your current profile directory first. It should be something like .mozilla/firefox/xxxxxxxx.default

---

### Post by jithin1987 on 2009-07-10
Creating a new profile works. Is there any way to fix my current one? It used to work 2 days back.

---

### Post by lovinglinux on 2009-07-10
> **jithin1987 said:**
> Creating a new profile works. Is there any way to fix my current one? It used to work 2 days back.

See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

---

### Post by jithin1987 on 2009-07-10
FOT002 - deleting localstore.rdf did not work out.

---

### Post by jithin1987 on 2009-07-10
I moved to a new profile, had my bookmarks, passwords and history from my old profile. Strange that things just break.

---

### Post by lovinglinux on 2009-07-10
> **jithin1987 said:**
> I moved to a new profile, had my bookmarks, passwords and history from my old profile. Strange that things just break.

Profiles get corrupted all the time. I reply to similar threads every day.

Sorry that my solution didn't work for you. I would proceed to another one, but creating a new profile also does the trick. To save yourself from the trouble in the future, make profile backups with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension. You can configure it to make regular backups. If  the profile gets corrupted, just restore the last backup.

---

### Post by jithin1987 on 2009-07-10
> **lovinglinux said:**
> Profiles get corrupted all the time. I reply to similar threads every day.

Sorry that my solution didn't work for you. I would proceed to another one, but creating a new profile also does the trick. To save yourself from the trouble in the future, make profile backups with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension. You can configure it to make regular backups. If  the profile gets corrupted, just restore the last backup.

Funny thing was that I tried FEBE also but its window was also blank. The solution you told was for blank addons window. In my case addons window was correct.

---

### Post by lovinglinux on 2009-07-11
> **jithin1987 said:**
> The solution you told was for blank addons window. In my case addons window was correct.

:oops: sorry for that. 

> **jithin1987 said:**
> Funny thing was that I tried FEBE also but its window was also blank.

Profiles cannot be restored using FEBE when they are active. You need to create a new blank profile, launch it, then install FEBE on it and restore the profile backup to your regular profile. It's kind of annoying, but it makes sense if you are trying to fix a profile that is completely corrupted.

---

### Post by tmahmood on 2010-03-24
Deleting the chrome folder's content solved the problem for me

---

