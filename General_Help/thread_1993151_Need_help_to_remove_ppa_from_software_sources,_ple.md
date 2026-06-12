---
title: "Need help to remove ppa from software sources, please."
date: 2012-06-01
forum: General Help
---

### Post by germanix on 2012-06-01
I added the following repository by using this command:
"sudo add-apt-repository ppa:diesch/testing"
I now want to remove this repository from my software sources but do not know which command to use to accomplish this?
Can anyone please assist?

---

### Post by MG&amp;TL on 2012-06-01
First remove/downgrade any packages you installed with said PPA.

Then post the output of:

```
ls /etc/apt/sources.list.d/
```

so we can tell you which ones to remove. :)

---

### Post by germanix on 2012-06-01
here is the information you asked for. Thank you for replying:
jacques@jacques-Viao:~$ ls /etc/apt/sources.list.d/
diesch-testing-precise.list
jacques@jacques-Viao:~$

---

### Post by MG&amp;TL on 2012-06-01
Run this command:

```
sudo rm /etc/apt/sources.list.d/diesch-testing-precise.list
```

then run:

```
sudo apt-get update
```

and you should be free of said PPA. :)


EDIT: ignore that, this way is much better (I should really be up to date with the times!):

```
sudo add-apt-repository -r ppa:diesch/testing
```

---

### Post by germanix on 2012-06-01
The command worked and the ppa was removed. This file is now no longer to be found under "etc/apt/sources.list.d". There is however now a new file in its place called  "diesch-testing-precise.list.save"?
Does not bother me at all, but I was just wondering why that is so?
As long as the ppa is removed, which it is, I am happy.
Thank you very much for your help. I appreciate it.

---

### Post by MG&amp;TL on 2012-06-01
> **germanix said:**
> The command worked and the ppa was removed. This file is now no longer to be found under "etc/apt/sources.list.d". There is however now a new file in its place called  "diesch-testing-precise.list.save"?
Does not bother me at all, but I was just wondering why that is so?
As long as the ppa is removed, which it is, I am happy.
Thank you very much for your help. I appreciate it.

Not a problem. 

My PPAs always have them, regardless if I've removed them or not. I don't know what they actually do.

---

### Post by Paqman on 2012-06-01
There's a GUI available that makes this pretty easy. It's called Software Sources and can either be pulled up on its own or through Software Centre, Update Manager and Synaptic.

---

### Post by germanix on 2012-06-02
Hi Paqman. thank you for this info. Will have a look. I missed this Gui in Unity. Have a nice day.

---

