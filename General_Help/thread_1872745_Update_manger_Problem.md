---
title: "Update manger Problem"
date: 2011-10-31
forum: General Help
---

### Post by x_mot on 2011-10-31
Hello
i'm using Ubunto 10.04
i have a problem with the update manger , here is a copy from the error.
[
Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

]

please be informed that its my first time to use Ubuntu , so if there is so basic things u are going to explain , please explain it briefly.
thanks in advance.


Assad

---

### Post by matt_symes on 2011-10-31
Hi

Open a terminal and type 

```
sudo rm -r /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen. Then type

```
sudo apt-get update
```

Kind regards

---

### Post by Rubi1200 on 2011-10-31
Hi and welcome to the forums x_mot :)

Just to clarify the excellent advice posted by matt_symes; the first command removes corrupted package lists, the second refreshes them.

If you run into any problems, let us know.

---

### Post by x_mot on 2011-10-31
thank both of you for the reply , things works great
:D 
i'm very happy for the fast response

---

### Post by matt_symes on 2011-10-31
Hi

> **Rubi1200 said:**
> Hi and welcome to the forums x_mot :)

Just to clarify the excellent advice posted by matt_symes; the first command removes corrupted package lists, the second refreshes them.

If you run into any problems, let us know.

Thanks for clarifying what the commands i posted actually do Rubi.

I think i should do that more. I was a bit rushed for time this morning though.

@OP. You have to be careful running any rm commands with elevated priviliges especially with the recursive switch. 

However, in this case, the command was designed to clear your list cache, as Rubi pointed out.

Kind regards

---

### Post by Rubi1200 on 2011-11-01
> **x_mot said:**
> thank both of you for the reply , things works great
:D 
i'm very happy for the fast response

Excellent! Glad this worked for you :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

