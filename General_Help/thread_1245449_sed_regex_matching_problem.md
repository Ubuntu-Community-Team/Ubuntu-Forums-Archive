---
title: "sed regex matching problem"
date: 2009-08-20
forum: General Help
---

### Post by treehouse on 2009-08-20
I'm trying to make a dynamic openbox menu using the output of openbox-xdgmenu. I'm attempting to replace the ampersands in that output with &amp; in order to make the output XML compliant. 

My script runs 
```

openbox-xdgmenu /etc/xdg/menus/applications.menu | sed 's/&/&amp;/'

```

but I run into a problem. I have a line in the output of openbox-xdgmenu that says 
```

<menu id="xdg-menu-Sound & Video" label="Sound & Video">

```

and it only replaces the first ampersand, so my output looks like this:
```

<menu id="xdg-menu-Sound &amp; Video" label="Sound & Video">

```

How do I get it to replace that second ampersand?

---

### Post by decoherence on 2009-08-20
> **treehouse said:**
> I'm trying to make a dynamic openbox menu using the output of openbox-xdgmenu. I'm attempting to replace the ampersands in that output with &amp; in order to make the output XML compliant. 

My script runs 
```

openbox-xdgmenu /etc/xdg/menus/applications.menu | sed 's/&/&amp;/'

```

but I run into a problem. I have a line in the output of openbox-xdgmenu that says 
```

<menu id="xdg-menu-Sound & Video" label="Sound & Video">

```

and it only replaces the first ampersand, so my output looks like this:
```

<menu id="xdg-menu-Sound &amp; Video" label="Sound & Video">

```

How do I get it to replace that second ampersand?

like so

sed 's/&/&amp;/g'

the 'g' means global (for that line)

---

### Post by geirha on 2009-08-20
Add the g flag to the substitution command

s/pattern/replacement/**g**

---

### Post by treehouse on 2009-08-20
That did it. Thanks bunches guys!

---

