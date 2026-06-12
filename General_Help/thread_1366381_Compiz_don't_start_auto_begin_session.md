---
title: "Compiz don't start auto begin session"
date: 2009-12-28
forum: General Help
---

### Post by clapton on 2009-12-28
Hello,

Compiz don't start automatic.

I've got fusion-icon, and I order to start fusion-icon -f.

Every time I login, I go to preferences, appearance and "No visual effects" is selected.
I choose extra, and it works. My configs at compiz advanced manager works just fine.

I've got docky with auto start. But without compiz, don't run the application.

---

### Post by KajuNM on 2009-12-28
I have the same problem, I wonder what's the problem, I hope someone on here can help.....

---

### Post by clapton on 2009-12-28
> **KajuNM said:**
> I have the same problem, I wonder what's the problem, I hope someone on here can help.....

Join the club!

I'm trying a solution. Replace advanced with simple compiz manager.

But it isn't a solution, is a alternative.

---

### Post by agnes on 2009-12-28
Do you've added the command "compiz --replace" to System->Preferences->Session? Before any other desktop stuff like docky is loaded.

---

### Post by clapton on 2009-12-28
> **agnes said:**
> Do you've added the command "compiz --replace" to System->Preferences->Session? Before any other desktop stuff like docky is loaded.

No! how can I determine the priority of execution?

---

### Post by agnes on 2009-12-28
You have to add that command there for compiz to autostart.

 I guess the default order is alphabetic. So if you add compiz --replace under the name and you have docky also in the list under the name "docky" or whatever, compiz will be before docky anyway because of that order.
If you suspect the order must be wrong (because docky is not working while you've added the compiz command, and compiz works, which suggests docky is loaded before compiz) take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1119945"). It explains how to set the autostart order precisely (see also [this thread]("http://ubuntuforums.org/showthread.php?t=1107749&page=2")).

---

### Post by clapton on 2009-12-29
> **agnes said:**
> You have to add that command there for compiz to autostart.

 I guess the default order is alphabetic. So if you add compiz --replace under the name and you have docky also in the list under the name "docky" or whatever, compiz will be before docky anyway because of that order.
If you suspect the order must be wrong (because docky is not working while you've added the compiz command, and compiz works, which suggests docky is loaded before compiz) take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1119945"). It explains how to set the autostart order precisely (see also [this thread]("http://ubuntuforums.org/showthread.php?t=1107749&page=2")).

I add compiz --replace and no compiz effects. I'll go to appearance and none effects is selected :(

---

### Post by microsome on 2010-01-29
Have the same issue. I have to start compiz using compiz --replace. Doing this in terminal, the temrminal freezes and I have to force quit. Nevertheless compiz is running afterwards. I reinstalled compiz, but this did not help.

Any suggestions?

---

