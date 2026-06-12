---
title: "echo redirection vs. text editor"
date: 2010-12-25
forum: General Help
---

### Post by MichaelBurns on 2010-12-25
I happen to have tried this in Xubuntu, but I assume that it is possibly a bash issue, rather than a desktop environment issue.

When I tried to create a file using redirection from the echo command, it denied my permission:
```

sudo echo "deb http://myrepo.int/ jaunty mycomponent" > /etc/apt/sources.list.d/myrepo.list

```
However, when I used the text editor to create and save the file, I had no problems:
```

sudo mousepad /etc/apt/sources.list.d/myrepo.list

```
Can someone explain to me why (bash?) is preventing me from creating the file using redirection from echo, and more relevantly, how can I do this using the redirection?  I want to be able to create the file from a script.  I prefer to get this working without installing yet another package.

---

### Post by WorMzy on 2010-12-25
Because your shell is trying to open the file (/etc/apt/sources.list.d/myrepo.list) before sudo is envoked (you may have noticed that you were not asked for your password, despite "sudo" being at the start of the command). I don't know of a direct way around this, but I recommend using

```
sudo -i
```
to get a root shell, then perform
```
echo "deb http://myrepo.int/ jaunty mycomponent" > /etc/apt/sources.list.d/myrepo.list
```

Alternatively, pipe echo into tee:
```
echo "deb http://myrepo.int/ jaunty mycomponent" | sudo tee /etc/apt/sources.list.d/myrepo.list
```

---

### Post by tredegar on 2010-12-25
This is how wretched sudo works.
Only the **echo** command is run as root, not the redirection part, so it fails.

One way to make it work is to become root, then give the command:
```
sudo -i
echo "deb [http://myrepo.int/](http://myrepo.int/) jaunty mycomponent" > /etc/apt/sources.list.d/myrepo.list
exit
```

---

### Post by MichaelBurns on 2010-12-27
Outstanding!  Thanks to both of you!

---

