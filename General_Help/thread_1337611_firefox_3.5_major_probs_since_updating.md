---
title: "firefox 3.5 major probs since updating"
date: 2009-11-25
forum: General Help
---

### Post by davewave918 on 2009-11-25
have been running 9.10 flawlessly for a few weeks now. very stoked on the new rev. then i was prompted to install updates. seems after that firefox has been working terribly. it hangs consistently and causes system instability. 

any help would be greatly appreciated. i have searched and located a few other threads here but nothing that specifically deals with this problem.

i would guess i should try un-installing/re-installing may be my 1st line of defense, but i am such a NOOB with ubuntu. i did "sudo aptitude purge firefox-3.5" and then apt-get install firefox-3.5 but i am not confident that it removed and reinstalled correctly and i still have the same problems. 










   [FONT=Arial]
[/FONT]

---

### Post by Divider on 2009-11-25
Could you be more specific with these problems your having?

---

### Post by tekkidd on 2009-11-25
try wiping your settings 

cd  /home/<username>/ 
rm -r .mozilla

that might work

---

### Post by davewave918 on 2009-11-25
> **Divider said:**
> Could you be more specific with these problems your having?


i will happily provide more info but i do not get any error messages. the browser is essentially unusable as it takes a while to load pages which are normally fast, navigation is slow. sometimes visiting different pages will take forever to load. while loading it can hang the browser and as well as other open applications which makes multitaksing while i am waiting also unbearable. before installing updates this was not an issue. my internet connection is fine. browsing on the same network from other hardware/os's is not an issue.

---

### Post by Divider on 2009-11-25
hmmm, that is weird, if I find anything I'll post it up.

---

### Post by davewave918 on 2009-11-25
much better now thx!


> **tekkidd said:**
> try wiping your settings 

cd  /home/<username>/ 
rm -r .mozilla

that might work

---

### Post by lovinglinux on 2009-11-25
> **tekkidd said:**
> try wiping your settings 

cd  /home/<username>/ 
rm -r .mozilla

that might work

I recommend the **mv** command instead of **rm**, so the user can get the data back if needed, like this:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox_backup
```

Otherwise, you should warn the user that he/she would loose all Firefox settings with the **rm** command. Besides, that might delete other Mozilla applications settings as well. To delete/move only Firefox profile data, use the folder **~/.mozilla/firefox** instead of just **~/.mozilla**

Nevertheless, you can usually fix Firefox profile related issues, by deleting just a single file from the profile folder or a couple of them. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for details. You can also fix several problems by performing regular backups and maintenance of Firefox profiles.

---

