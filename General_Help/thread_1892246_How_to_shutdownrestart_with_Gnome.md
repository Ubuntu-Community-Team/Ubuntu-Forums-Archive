---
title: "How to shutdown/restart with Gnome"
date: 2011-12-07
forum: General Help
---

### Post by IanVaughan on 2011-12-07
I've started using the new Gnome, but I cannot find Shutdown or Restart?

Under my username I have the following options :-

Lock Screen
Switch User
Log out

Suspend


Do they not think that shutting down or restarting a computer would be necessary?

---

### Post by BC59 on 2011-12-07
Install this extension:

```
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-alternative-status-menu
```

Then use Gnome Tweak Tool to enable the extension.

---

### Post by qamelian on 2011-12-07
> **IanVaughan said:**
> I've started using the new Gnome, but I cannot find Shutdown or Restart?
 
Under my username I have the following options :-
 
Lock Screen
Switch User
Log out
 
Suspend
 
 
Do they not think that shutting down or restarting a computer would be necessary?
 Hold down the Alt key and Suspend will change to Shutdown.

---

### Post by IanVaughan on 2011-12-07
> **BC59 said:**
> Install this extension:

```
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-alternative-status-menu
```

Then use Gnome Tweak Tool to enable the extension.

I did this, but cannot find the tool!?
Im on 11.10.

---

### Post by IanVaughan on 2011-12-07
> **qamelian said:**
> Hold down the Alt key and Suspend will change to Shutdown.

AHHH! Many thanks!

What about Reboot?

I see they've employed some Apple UI "experts" then! 
Hiding menu options so we have to waste time figuring them out. AHHH

---

### Post by BC59 on 2011-12-07
I thought that you have installed it already. It's a basic tool of tweaking Ubuntu 11.10.

You can install it from Ubuntu software center, where you have to search it as **Advanced Settings**.

---

### Post by IanVaughan on 2011-12-07
> **BC59 said:**
> I thought that you have installed it already. It's a basic tool of tweaking Ubuntu 11.10.

You can install it from Ubuntu software center, where you have to search it as **Advanced Settings**.

Ahh, ok, I searched for "Advanced Settings", and wow, thats exactly what I was looking for!

Even solved another problem I was going to post for, getting Min/Max window buttons back!!!

Many thanks!

---

### Post by qamelian on 2011-12-07
> **IanVaughan said:**
> AHHH! Many thanks!
 
What about Reboot?
 
I see they've employed some Apple UI "experts" then! 
Hiding menu options so we have to waste time figuring them out. AHHH
 When you click on Shutdown, a confirmation dialog box appears that has buttons for Shutdown, Restart, and Cancel.

---

### Post by IanVaughan on 2011-12-07
> **qamelian said:**
> When you click on Shutdown, a confirmation dialog box appears that has buttons for Shutdown, Restart, and Cancel.

I think the best solution/answer was to install "Advanced Settings"!

Thanks to all!

---

### Post by Deuce1912 on 2011-12-07
The easiest way is to use the new extensions website by gnome. Check out the following link to activate the Shutdown features with one click. (I believe you have to be using firefox to install them.) There is roughly four pages of other extensions that you can install.

[https://extensions.gnome.org/extension/14/shut-down-menu/](https://extensions.gnome.org/extension/14/shut-down-menu/)

- Deuce

---

### Post by IanVaughan on 2011-12-07
> **Deuce1912 said:**
> The easiest way is to use the new extensions website by gnome. Check out the following link to activate the Shutdown features with one click. (I believe you have to be using firefox to install them.) There is roughly four pages of other extensions that you can install.

[https://extensions.gnome.org/extension/14/shut-down-menu/](https://extensions.gnome.org/extension/14/shut-down-menu/)

- Deuce

"Shell Extensions"!
How cool is that!
Thanks.

---

### Post by Deuce1912 on 2011-12-07
> **IanVaughan said:**
> "Shell Extensions"!
How cool is that!
Thanks.

No problem. Just doing what I can to help others. Lord knows I've learned so much more here on these forums than I have given back.

- Deuce

---

