---
title: "Running &quot;Sudo firefox&quot; killed firefox???!"
date: 2009-07-04
forum: General Help
---

### Post by brad1138 on 2009-07-04
I ran "sudo firefox" from terminal so that the "check for updates" option would not be greyed out. It worked but still didn't list 3.5 as an upgrade. So I closed the sudo firefox, but now when I click my FF link, FF comes up with no bookmarks, no theme, all the Google tool-bar buttons are gone or grayed out. It wont search from the Google search bar or Google web page. I seem to have killed it. If I run Sudo FF again, everything works fine, all my bookmarks are there etc...

Any ideas?
Brad

---

### Post by pokerbirch on 2009-07-04
Google for "Firefox Profile Manager".

---

### Post by wojox on 2009-07-04
Use gksu to run graphical tools.

root now owns some of your Firefox

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

<user_name> is your username

---

### Post by aysiu on 2009-07-04
> **wojox said:**
> Use gksu to run graphical tools.

root now owns some of your Firefox

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

<user_name> is your username
That's a good fix.

You should never run *sudo* with a graphical application. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lovinglinux on 2009-07-04
See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by brad1138 on 2009-07-04
> **wojox said:**
> Use gksu to run graphical tools.

root now owns some of your Firefox

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

<user_name> is your username

That seems to have worked. I don't understand Linux well enough to understand what that just did, I kind of get the "Sudo now owns part of my ff" but not why. Anyway, I won't do that again.

Thanks,
Brad

---

### Post by aysiu on 2009-07-04
> **brad1138 said:**
> That seems to have worked. I don't understand Linux well enough to understand what that just did, I kind of get the "Sudo now owns part of my ff" but not why. Anyway, I won't do that again.

Thanks,
Brad
That command **ch**anges **own**ership of your Firefox profile back to you.

When you ran the command *sudo firefox*, you ran Firefox with system-wide permissions but with your user profile, so it changed your Firefox profile from user ownership to root ownership.

If you ever have to run Firefox as root, you should use ```
gksudo firefox
``` and not *sudo firefox*. The only case in which you would run Firefox as root is to update it if you're using [the Firefox downloaded from Mozilla](http://www.psychocats.net/ubuntu/firefox) and not the Ubuntu repositories Firefox.

---

### Post by Viva on 2009-07-04
When you run firefox as sudo, it changes the permissions of your preferences file(javascript), so you can't access it as a normal user.

---

### Post by Primefalcon on 2009-07-04
I did this myself when I first started using Ubuntu, I suspect a lot of people have...

---

### Post by aysiu on 2009-07-04
> **Viva said:**
> When you run firefox as sudo, it changes the permissions of your preferences file(javascript), so you can't access it as a normal user.
JavaScript?

---

### Post by Viva on 2009-07-04
> **aysiu said:**
> JavaScript?

Apologies, I was referring to the prefs.js file. I think I need to go to bed now, too late in the night and my mind isn't working properly:lolflag:

---

### Post by aysiu on 2009-07-04
> **Viva said:**
> Apologies, I was referring to the prefs.js file. I think I need to go to bed now, too late in the night and my mind isn't working properly:lolflag:
Ah, that makes more sense. That is one file in the /home/username/.mozilla folder, but I think it's more than just that file that changes ownership if you run *sudo firefox*. Get some rest... we all need that sometimes.

---

