---
title: "Problem with &quot;sudo apt-get update &amp;&amp; upgrade&quot;"
date: 2011-12-17
forum: General Help
---

### Post by iosuna86 on 2011-12-17
The issue is pretty simple. I am using **Ubuntu 11.10** and whenever I run the command:

```
sudo apt-get update && upgrade
```

the following message appears:

```
...
Fetched xxx B in xxs (xxx B/s)
Reading package lists... Done
**upgrade: command not found**
```

The thing is that since I installed Oneiric I have to run 

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

one after the other.

It is not a big issue, but I do not understand what could be behind it. Any thoughts? 

Thanks in advance!

---

### Post by sunfromhere on 2011-12-17
Try this one:

```
sudo apt-get update && sudo apt-get upgrade
```

Works for me (11.10)

EDIT: yup, just tested your version, shows the same error.

---

### Post by iosuna86 on 2011-12-17
> Try this one:

```
sudo apt-get update && sudo apt-get upgrade
```

Works for me (11.10)

Yeah! That's it!

I don't get the point on changing the command, though.

Thank you!

---

### Post by Lars Noodén on 2011-12-17
> **iosuna86 said:**
> I don't get the point on changing the command, though.


Think of it like this:

```

(sudo apt-get update) && (sudo apt-get upgrade)

```

---

