---
title: "Change suspend-when-active to something I want"
date: 2012-07-29
forum: General Help
---

### Post by Paddy Landau on 2012-07-29
I go to System Settings > Power > Suspend when inactive for...

I get just five choices: Never, 5 minutes, 10 minutes, 30 minutes, and one hour.

That is too limiting for me. (Why, oh why, do suspend programs -- not just computers, but also radio clocks and the like -- assume that they know the range that you could ever need?)

I am in fact after 2:30, because 2 hours is too short and 3 hours too long.

How can I change the suspend wait to a different value?

---

### Post by Paddy Landau on 2012-07-30
Bump!

---

### Post by vasa1 on 2012-07-30
Xfce's power manager has a slider up to 5 hours 50 min with 1 min as the least count.

---

### Post by Paddy Landau on 2012-07-30
OK, I'm jealous. That sounds like an excellent way to do it.

Unfortunately, I use Unity, not XFCE, so that doesn't help.

---

### Post by vasa1 on 2012-07-31
> **Paddy Landau said:**
> ... Unfortunately, I use Unity, not XFCE, so that doesn't help.
Just saw this while searching for something else!

Why don't you ask [quidsup]("http://www.youtube.com/user/quidsup"). He posts a lot of very decent videos dealing with Unity on YouTube. I've even seen some in which he pokes around in d- and gconf. He comes across as knowledgeable **and responsive**. Plus he's in your corner of the world so you can buy him a pint :)

(My point is that this dconf/gconf thing may give you finer control?)

---

### Post by vasa1 on 2012-08-01
In dconf-editor,
org.gnome.settings-daemon.plugins.power,
there's "sleep-inactive-ac-timeout".
Maybe that's what you want? Under Type, there is integer [-2147483648..2147483647] whatever that means ???

---

### Post by Paddy Landau on 2012-08-01
> **vasa1 said:**
> org.gnome.settings-daemon.plugins.power, ... "sleep-inactive-ac-timeout"
That's it, thank you I haven't tested it yet, but I shall do so later today.
> **vasa1 said:**
> Under Type, there is integer [-2147483648..2147483647] whatever that means ???
It means that the value values are anything from -2,147,483,648 (a negative value? It means suspend *before* the machine is idle and assumes that the computer can predict the future :shock:) to 2,147,483,647 seconds (a bit over 68 years, LOL).

---

