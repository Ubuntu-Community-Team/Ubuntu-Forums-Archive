---
title: "How to remove manually installed applications?"
date: 2011-01-23
forum: General Help
---

### Post by aisajib on 2011-01-23
We all know that we can remove installed applications straight from terminal or ubuntu software center. However, sometimes we download .deb files from the web that are not necessarily on the repository. My question is, how do I uninstall a manually installed deb application?

I hope I have been clear about my query. Thanks for any help in advance.

---

### Post by pqwoerituytrueiwoq on 2011-01-23
look in Synaptic

---

### Post by MooPi on 2011-01-23
Use ```
sudo dpkg -r application_name
``` to uninstall

---

### Post by Frogs Hair on 2011-01-23
System > Adminisration > Synaptic Package Manager > installed (local or obsolete)

Right click on the line of the package to be removed select mark for complete removal and select apply.

You can also use the search box to locate the package.

---

### Post by aisajib on 2011-01-23
> **MooPi said:**
> Use ```
sudo dpkg -r application_name
``` to uninstall

Where do I get the application name? Because sometimes the name of the application is not what used in the terminal (unlike firefox for Mozilla Firefox).

> **Frogs Hair said:**
> System > Adminisration > Synaptic Package Manager > installed (local or obsolete)

Right click on the line of the package to be removed select mark for complete removal and select apply.

You can also use the search box to locate the package.

That kind of helps. Thanks.

---

### Post by corncob on 2011-01-23
> **aisajib said:**
> We all know that we can remove installed applications straight from terminal or ubuntu software center. However, sometimes we download .deb files from the web that are not necessarily on the repository. My question is, how do I uninstall a manually installed deb application?

I hope I have been clear about my query. Thanks for any help in advance.

I find these applications to be listed in Systems > Administration > Computer Janitor.  Be sure to uncheck any apps that you don't want to remove.

---

### Post by MooPi on 2011-01-23
This command will give you all packages installed. ```
dpkg --get-selections
```
I use this command to generate a text file of all installed. ```
dpkg --get-selections>installed
```
To find the package just [COLOR="Blue"]Ctrl + f[/COLOR] that document

---

### Post by aisajib on 2011-01-23
> **corncob said:**
> I find these applications to be listed in Systems > Administration > Computer Janitor.  Be sure to uncheck any apps that you don't want to remove.

Hey thanks there. I have been to Computer Janitor but I thought it only listed up leftover files of removed applications. Never knew that it includes installed apps, too. Anyway, good that we can delete apps from janitor, too. Thanks for your help.

> **MooPi said:**
> This command will give you all packages installed.  ```
dpkg --get-selections
```I use this command to generate a text  file of all installed. ```
dpkg  --get-selections>installed
```

Thanks! I do see a list of installed apps. However, the latter code didn't generate the list on a text file. In fact, it did nothing.

Not a problem, though. :)

---

### Post by corncob on 2011-01-23
> **aisajib said:**
> Hey thanks there. I have been to Computer Janitor but I thought it only listed up leftover files of removed applications. Never knew that it includes installed apps, too. Anyway, good that we can delete apps from janitor, too. Thanks for your help.
 :)

Computer Janitor doesn't do what its supposed to do --- it wants to remove 3rd party applications even while they're in use!  I thought that might be handy in this case.

---

### Post by aisajib on 2011-01-23
> **corncob said:**
> Computer Janitor doesn't do what its supposed to do --- it wants to remove 3rd party applications even while they're in use!  I thought that might be handy in this case.

Yes, I would want it to remove apps that are already in use. However, in my case, it came helpful. :D

---

### Post by matt_symes on 2011-01-23
Hi

```
dpkg --list
```

to list installed packages with a description helps.

Kind regards

---

### Post by aisajib on 2011-01-23
> **matt_symes said:**
> Hi

```
dpkg --list
```to list installed packages with a description helps.

Kind regards

Thanks so much. That's more easy to remember.

Off-topic: How exactly does Google Linux work?

---

### Post by matt_symes on 2011-01-23
Hi

Type into your browser

```
www.google.com/linux
```

It will display the Google's Linux search engine that is tailored to return results about Linux. It can help remove erroneous search results that do not relate to Linux. 

It comes complete with Tux :D

Kind regards

---

