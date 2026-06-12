---
title: "Default Browser"
date: 2009-09-12
forum: General Help
---

### Post by Hosmion on 2009-09-12
Is there a way to make another browser besides Firefox your default browser?

---

### Post by DeMus on 2009-09-12
> **Hosmion said:**
> Is there a way to make another browser besides Firefox your default browser?

Look in System --> Preferences --> Preferred application.

---

### Post by Hosmion on 2009-09-12
I only have Firefox and custom as my choices, I want to use Epiphany Web Browser as my default..  No option to add that..

---

### Post by SuperSonic4 on 2009-09-12
Custom means you get to choose. Click custom and select ```
/usr/bin/epiphany
```

---

### Post by khelben1979 on 2009-09-12
You can try what has been described [on this page]("http://www.novell.com/coolsolutions/feature/8974.html") from Cool Solutions.

---

### Post by Hosmion on 2009-09-12
> **SuperSonic4 said:**
> Custom means you get to choose. Click custom and select ```
/usr/bin/epiphany
```
It doesn't give me the option to browse (see attachment)

---

### Post by SuperSonic4 on 2009-09-12
What happens if you click in that drop down menu? (I do not use gnome so I can't help) >.<

---

### Post by wojox on 2009-09-12
Put:

```
epiphany "%s"
```

In custom.

---

### Post by Hosmion on 2009-09-12
> **wojox said:**
> Put:

```
epiphany "%s"
```In custom.
Did that and it still does not work (see attachment)

---

### Post by wojox on 2009-09-12
Copy and paste my command. It needs the quotes.

---

### Post by Hosmion on 2009-09-12
Still opens with Firefox.

---

### Post by paradigm2 on 2009-09-12
> **Hosmion said:**
> Still opens with Firefox.

Some applications have their own means of selecting the browser to use?  For example in checkgmail you have to right click, then select preferences and change it.

What are you using to try to bring up the default browser?  Another application?  The browser key on your keyboard? etc?

---

### Post by Hosmion on 2009-09-12
> **paradigm2 said:**
> Some applications have their own means of selecting the browser to use?  For example in checkgmail you have to right click, then select preferences and change it.

What are you using to try to bring up the default browser?  Another application?  The browser key on your keyboard? etc?
I'm trying to make it so when I hit a shortcut on my desktop it opens with Epiphany Web Browser

---

### Post by wojox on 2009-09-12
Then change the shortcut command.

---

### Post by paradigm2 on 2009-09-12
> **Hosmion said:**
> I'm trying to make it so when I hit a shortcut on my desktop it opens with Epiphany Web Browser

Do you have Epiphany installed?  On my default Ubuntu install Ephiany isn't installed.


To check go to a terminal and type

```

epiphany

```

Does it come up?

If not, Go into Synaptic (or elsewhere or follow the command suggested) and install it.

```

The program 'epiphany' is currently not installed.  You can install it by typing:
sudo apt-get install epiphany-browser

```

Then once installed try going into preferred applications again. :)

---

