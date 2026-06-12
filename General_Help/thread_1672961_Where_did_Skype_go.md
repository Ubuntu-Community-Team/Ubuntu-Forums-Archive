---
title: "Where did Skype go?"
date: 2011-01-21
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-21
Last time I could install Skype from the Software Center but now it is not listed there no more. What is that about?

---

### Post by earthmeLon on 2011-01-21
> **Crux_Dissimilata said:**
> Last time I could install Skype from the Software Center but now it is not listed there no more. What is that about?

Searched google for "ubuntu skype" and got this:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

### Post by khjinn on 2011-01-21
Did you enable canonical in software sources?

```
Right click "Applications" > Edit Menu > Scroll down and click Administration on the left > Put a check next to Software Sources
```

Then

```
System > Admin > software sources > switch to the Other Software tab > check all
```

Then

In terminal ... 

```
sudo apt-get update
```


Skype should be in Software Center now.

---

