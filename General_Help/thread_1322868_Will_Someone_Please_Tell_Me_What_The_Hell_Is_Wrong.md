---
title: "Will Someone Please Tell Me What The Hell Is Wrong With This?"
date: 2009-11-11
forum: General Help
---

### Post by Mark76 on 2009-11-11
From my openbox rc file

> <application>
<application name=Gdeskcal>
class=gdeskcal
type=desktop
>
<desktop>all</desktop>
<layer>below</layer>
</application>

---

### Post by fela on 2009-11-11
What's the > on its own for?

---

### Post by Mark76 on 2009-11-11
I forgot about it

Can someone please show me how to do this properly?

I'm trying to make an application not disappear when I use show desktop, and also to not have shadows around it.

---

### Post by Mark76 on 2009-11-11
This is what I meant it it look like

> <application>
<application name=gdeskcal
class=gdeskcal
type=dock/>

<decor>no</decor>
<desktop>all</desktop>
<layer>normal</layer>
</application>

And the attachment shows what I get

---

### Post by Vaphell on 2009-11-11
i looked at 
[http://git.icculus.org/?p=mikachu/openbox.git;a=blob;f=data/rc.xml;hb=3.4-working](http://git.icculus.org/?p=mikachu/openbox.git;a=blob;f=data/rc.xml;hb=3.4-working)
and you messed up the tags

apparently you should have
<applications>
  <application param=paramvalue ... >
    <stuff>...</stuff>
    ...
  </application>
</applications>

/ at the end closes the application tag ( <app />) but other things should be embedded inside (<app><stuff></stuff></app>)

---

### Post by bostonaholic on 2009-11-11
> **Mark76 said:**
> From my openbox rc file

here:

```
<applications>
    <application name=Gdeskcal
        class=gdeskcal
        type=desktop/>
    <desktop>all</desktop>
    <layer>below</layer>
</applications> 
```

---

### Post by jeb800e on 2009-11-11
Well, something is definately wrong with the application "Gdeskcal"

---

### Post by Mark76 on 2009-11-11
> **Vaphell said:**
> i looked at 
[http://git.icculus.org/?p=mikachu/openbox.git;a=blob;f=data/rc.xml;hb=3.4-working](http://git.icculus.org/?p=mikachu/openbox.git;a=blob;f=data/rc.xml;hb=3.4-working)
and you messed up the tags

apparently you should have
<applications>
  <application param=paramvalue ... >
    <stuff>...</stuff>
    ...
  </application>
</applications>

/ at the end closes the application tag ( <app />) but other things should be embedded inside (<app><stuff></stuff></app>)

Okay, I amended that and got this

---

### Post by Mark76 on 2009-11-11
No change I make seems to work :(

I don't get it. I don't get it, I don't get it, I don't get it :mad:

---

### Post by bostonaholic on 2009-11-11
> **Mark76 said:**
> No change I make seems to work :(

I don't get it. I don't get it, I don't get it, I don't get it :mad:

Rechecked mine, maybe it needs quotes?  try

```
<applications>
    <application name="Gdeskcal"
        class="gdeskcal"
        type="desktop">
        <desktop>all</desktop>
        <layer>below</layer>
    </application>
</applications>
```

---

### Post by Mark76 on 2009-11-11
I'm not sure that helped.  The pop up has gone but the window still disappears when I click on show desktop

---

### Post by Vaphell on 2009-11-11
lack of popup means that the config file is not malformed. Actual working configuration is an entirely different beast :-)

---

