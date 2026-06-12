---
title: "Compiz Switch"
date: 2010-07-03
forum: General Help
---

### Post by Tumpster on 2010-07-03
Hey there, I stumbled across this great piece of software many moons ago and have been using it to help shut my compiz off to improve or minimize my troubles graphically in games. I'm looking to see if theres an updated one for 10.04? Thanks!

---

### Post by darolu on 2010-07-03
[Quote="Forlong's Blog]Compiz runs differently on Ubuntu 10.04 Lucid Lynx.
I don't have the time to upload a new package right now, but here's how you can fix the script after you have installed the deb above on Lucid:

sudo sed 's/\.real//g' -i /usr/bin/compiz-switch[/Quote]

Read it all and download compiz-switch here: [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by Tumpster on 2010-07-03
> **darolu said:**
> Read it all and download compiz-switch here: [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

It's dated 6/1/2008, theres nothing newer?

---

### Post by darolu on 2010-07-04
Did you read the part I quoted? It says and I quote again (just without the quote wrap): "Compiz runs differently on **Ubuntu 10.04 Lucid Lynx**.
I don't have the time to upload a new package right now, but **here's how you can fix** the script after you have installed the deb above on **Lucid**:

**sudo sed 's/\.real//g' -i /usr/bin/compiz-switch**"

---

### Post by Tumpster on 2010-07-04
> **darolu said:**
> Did you read the part I quoted? It says and I quote again (just without the quote wrap): "Compiz runs differently on **Ubuntu 10.04 Lucid Lynx**.
I don't have the time to upload a new package right now, but **here's how you can fix** the script after you have installed the deb above on **Lucid**:

**sudo sed 's/\.real//g' -i /usr/bin/compiz-switch**"

Dont mind me, I'm an idiot. I will look into it!

---

