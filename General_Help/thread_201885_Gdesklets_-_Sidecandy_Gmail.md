---
title: "Gdesklets - Sidecandy Gmail"
date: 2006-06-22
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-22
I installed the Sidecandy Gmail notifier and when it won't recognize any new messages in my gmail inbox. When I start it up, an error occurs, see screenshots.

I typed all my e-mail information, but it still doesn't work. 

Does anyone know what this means/ how to fix it?

---

### Post by FaceLeg on 2007-05-25
I get the same...

---

### Post by jimbob on 2007-05-25
I have found lots of those desklets that flat out don't work.  Maybe this is one of them.

Does anyone out there have this on installed and working?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Fakircho on 2007-06-17
I am also having trouble with this
I have a couple of sidecandy gdesklets and they work fine 
I have noticed that the gmail one however does not install in the same way 
In the manager you can see that every deslket installs in the /user/lib ...... and so on 
The Gmail one has a path like /home/name ..... and so on 

i wonder if that is the problem? I do not how to fix this, any ideas ?

---

### Post by SecrethX on 2007-07-23
Can anybody send me this desklet? I can _try_ to fix it..

---

### Post by Fakircho on 2007-07-24
[http://www.linspire.com/lindows_products_details.php?product_id=21418&pg=specs](http://www.linspire.com/lindows_products_details.php?product_id=21418&pg=specs)

You can find it here. If have any success please post back a version that works on Ubuntu :) Thanks

---

### Post by SecrethX on 2007-07-24
Seems that you need to find a control named 'gmail' it isnt in the default package anymore but ill search.
```
<control id="mail" interface="IGmail:d4fjyzvgb0ejso27f3g1j5c7k"/>
```

I'll post here if I find it.

EDIT: Google pages come up empty.. :S

EDIT2: Since it is still on the linspire site, the control has to be in the gdesklet package of linspire. I'll try to find that one instead.

---

### Post by Stryker777 on 2008-05-03
Interstingly enough, I can use a secondary gmail account and it works fine but my normal one will not.  I thought it had something to do with my password characters but I changed them to the same thing and it still did not work.  I am now of the opinion that it has something to do with how long ago you logged in or something.  That is the only difference in the two accounts.

---

### Post by dmitrievich on 2008-06-12
Copy folder "controls/Gmail" from archive to the "/usr/share/gdesklets/Controls"

---

### Post by Stryker777 on 2008-06-12
I wish it did, but that did not fix it either.  It is really funny that it is only one of my accounts though lol.  Thanks though!

---

### Post by gardara on 2008-06-13
Gdesktlets is outdated! Take a look at ScreenLets [http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

---

### Post by lisati on 2008-06-13
> **Stryker777 said:**
> Interstingly enough, I can use a secondary gmail account and it works fine but my normal one will not.  I thought it had something to do with my password characters but I changed them to the same thing and it still did not work.  I am now of the opinion that it has something to do with how long ago you logged in or something.  That is the only difference in the two accounts.

Could gmail's pop/forwarding settings be different for your two accounts?

---

### Post by Stryker777 on 2008-06-13
Good idea but no.  On both accounts, all settings are exactly the same.  Oh well.  I dont really need the screenlet.  Just wanted to show off to the few friends that are still stuck on Windblows lol.

---

