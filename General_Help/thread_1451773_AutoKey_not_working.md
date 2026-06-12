---
title: "AutoKey not working??"
date: 2010-04-11
forum: General Help
---

### Post by pakki on 2010-04-11
First of all i hav 2 icon in my accessories panel AutoKey(GTK) & AutoKey (QT)
Whichever i run ths pops up
[IMG]http://i41.tinypic.com/4q3a4k.jpg[/IMG]
i cannot make autokey work
it opens afterwards wth full interface; i can add phrases set abbreviations & hotkeys etc but it just doesnt produce required results when typing in notepad office or firefox etc...

What am i missing

---

### Post by glisten on 2010-05-24
Me too. It was working fine, then bang.

Thanks,
Jim
Dell 4800, Lucid Lynx.

---

### Post by cdekter on 2010-07-06
If anyone is still having trouble, I'd be happy to help out (I'm the main dev of AutoKey).

---

### Post by dt_matthews on 2010-09-11
> **cdekter said:**
> If anyone is still having trouble, I'd be happy to help out (I'm the main dev of AutoKey).

I'm running Lucid and Autokey works ok for a while then just stops expanding my abbreviations, if i kill it then start a new instance it works ok (for a bit). I havent been able to ascertain what causes it to stop working and I dont get any errors or notifications of a problem.

If you can let me know what debug info I can provide then feel free! 

cheers,
dan

---

### Post by thaelim on 2010-09-11
There is a wiki page [here]("http://code.google.com/p/autokey/wiki/Troubleshooting") on troubleshooting and how to get debug information.

---

### Post by exit_jones on 2010-10-01
unfortunately, i'm seeing the same thing.  i'm running 64-bit lucid and autokey works perfectly-- then stops working.  i have been to the aforementioned troubleshooting page, but there's nothing that really addresses this issue, as there are no outward symptoms at all (the autokey GUI does not behave differently from normal).

EXCEPT, notably: when i run:
```
$ autokey-gtk -l
```
for debug mode, and then try any of my hotkeys or text-expansion abbreviations, there is no output at all (in the terminal, let alone the deired text expanision or action).  it seems that the autokey daemon just stops running.  i do get the standard messages in my terminal under debug mode when i create a new phrase or save something, but again, it's as if AK is not listening for input at all.

while in the current gdm session i could do nothing to get it to work... in the heat of the moment i got around it by running autokey as root (which i figure worked because it is another session, not because it's root), but that's really unsavory.

does anyone have an idea for troubleshooting further?

btw, mr dekter, fantastic work.  when it's working, it has only one flaw (inability to edit the config file directly, no gui)... and other than that, this is the greatest productivity tool since earplugs.

---

