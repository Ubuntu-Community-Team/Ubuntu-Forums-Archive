---
title: "Uninstalling Programs"
date: 2006-05-30
forum: General Help
---

### Post by evandec on 2006-05-30
How can I unistall programs. I just tried to uncheck the program where you add them but it told me I need to find the advanced settings....

Im not sure where those are.

---

### Post by aysiu on 2006-05-30
**Advanced Settings**:
System > Administration > Synaptic Package Manager

You may want to also read:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by tonyr on 2006-05-30
What tool are you using? Synaptic? Adept? Aptitude? Command line in a
terminal?

If you are using a terminal, you can do
```

sudo apt-get remove  <package-name>

```

If you are using Synaptic, right-click the package name in the listing, and you should 
get a drop-down menu of options, one of which says something like
**Request removal**.

---

### Post by tonyr on 2006-05-30
[QUOTE=aysiu]**Advanced Settings**:
System > Administration > Synaptic Package Manager
[/QUOTE]

Does **Breezy** not have the **Advanced** button in the **Add/Remove** tool,
or maybe a different Add/Remove tool altogether? (I started with Dapper,
so what the heck do I know?).

---

### Post by tomo-boss on 2006-06-25
thanks this helped me
:mrgreen:

---

