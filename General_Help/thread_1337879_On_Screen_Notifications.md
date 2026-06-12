---
title: "On Screen Notifications"
date: 2009-11-25
forum: General Help
---

### Post by tom.swartz07 on 2009-11-25
Hi all

What is the command to create one of the black notification popups?
I used to use the command for my checkgmail all of the time, but for some reason it has been changed for 9.10

```
notify-send "You have %m New $mess" -i ~/bin/gmail.png
```
Used to give me a notification when I received a message.
How does one translate 'notify-send' to whatever the new notification program uses?

Thanks!

---

### Post by kaibob on 2009-11-25
> **tom.swartz07 said:**
> What is the command to create one of the black notification popups?
It's still notify-send. Just to check, I ran the following, which worked fine.
```
notify-send -i info "Test"
```
Probably a dumb question, but did you remember to install the necessary software package? I believe it's libnotify-bin

---

### Post by tom.swartz07 on 2009-11-25
> **kaibob said:**
> It's still notify-send. Just to check, I ran the following, which worked fine.
```
notify-send -i info "Test"
```
Probably a dumb question, but did you remember to install the necessary software package? I believe it's libnotify-bin

Not a really dumb question- I wasnt sure that I needed it, as I had the notifications to begin with! It seems counter-intuitive that you need to install the extra package to manipulate the notifications that you already receive!

Works great now! Thanks a ton!

---

