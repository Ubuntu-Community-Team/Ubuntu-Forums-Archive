---
title: "Comon Ubuntu..."
date: 2010-05-11
forum: General Help
---

### Post by tripower on 2010-05-11
I have Ubuntu 9.10 Karmic (64 bit) running on a Toshiba U305 laptop. I have a few issues:

1. If I don't explicitly lock the computer and close the top of the laptop, sometimes it locks the computer sometimes it doesn't and it never locks right away after I close the top of the computer.

2. I have set and reset the power settings numerous times (to always stay on when connected to AC), and yet it still fades to power down after inactivity. And to me the fading is not a smooth transition.

3. Copy and paste works intermittently.

Most of these look like bugs, how do I report bugs?

---

### Post by 3rdalbum on 2010-05-11
> **tripower said:**
> 3. Copy and paste works intermittently.

Closing a program will also remove the contents of its clipboard. It's a bad design but not a bug. Use Glipper - install it and add it to your panel and it will preserve the contents of your clipboard.

> Most of these look like bugs, how do I report bugs?

Create an account on [www.launchpad.net](www.launchpad.net), first.

Try and find a likely package that your bug belongs to - for instance, gnome-power-manager.

Run the command:

```
apport-bug gnome-power-manager
```

Follow the prompts. All relevant log files will be collected and submitted. Describe in the bug report what you are doing to cause the bug's appearance, what you expected to happen and what actually happened, and any other information that may help.

---

### Post by junapp on 2010-05-11
> **tripower said:**
> 
2. I have set and reset the power settings numerous times (to always stay on when connected to AC), and yet it still fades to power down after inactivity. And to me the fading is not a smooth transition.


I noticed the same thing, but it is only while on AC power but not charging. I've got a little light that is on while the battery is charging. When I am on AC power, but that light is off, my screen fades as well.

---

### Post by tripower on 2010-05-12
> **3rdalbum said:**
> Closing a program will also remove the contents of its clipboard. It's a bad design but not a bug. Use Glipper - install it and add it to your panel and it will preserve the contents of your clipboard.



Create an account on [www.launchpad.net]("http://www.launchpad.net"), first.

Try and find a likely package that your bug belongs to - for instance, gnome-power-manager.

Run the command:

```
apport-bug gnome-power-manager
```Follow the prompts. All relevant log files will be collected and submitted. Describe in the bug report what you are doing to cause the bug's appearance, what you expected to happen and what actually happened, and any other information that may help.


How do I report a bug for Ubunto 9.10 on launchpad.net?

---

### Post by 3rdalbum on 2010-05-12
> **tripower said:**
> How do I report a bug for Ubunto 9.10 on launchpad.net?

Exactly the same way.

---

