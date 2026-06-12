---
title: "Removing menu from &quot;software-center&quot; added by &quot;redeclipse&quot;"
date: 2011-09-30
forum: General Help
---

### Post by LinTux on 2011-09-30
I installed the redeclipse package with these steps
```

sudo add-apt-repository ppa:itachi-sama-amaterasu/redeclipse-client
sudo apt-get update
sudo apt-get install redeclipse

```
It added the menu that is present in the screenshot attached to this post. This was fine, but when i uninstalled 
```

sudo apt-get remove redeclipse-svn-data

```
(which had all the data. It's removal also removed the "redeclipse-svn-data" and "redeclipse-svn")

This did not remove the menu so i tried
```

sudo apt-get autoremove

```
It did not work, so i tried reinstalling "software-center" from the synaptic package manager. That did not work

How can i remove that from the menu? It is annoying.

---

### Post by LinTux on 2011-09-30
After doing some reasearch, if found 2 things

1. that i had not actually used ```

sudo add-apt-repository ppa:itachi-sama-amaterasu/redeclipse-client

```
but i used
```
sudo add-apt-repository ppa:arand/redeclipse
```

2. I figured out a few minutes after the post that the menu in the software center was actually the repository i had added. i realized that i could have just removed it. I did it with
```
sudo add-apt-repository **-r** ppa:arand/redeclipse
```




Sorry to have bothered all of you.:oops:

](*,)

---

### Post by papibe on 2011-09-30
The command add-apt-repository works different than regular apt-get. You are adding an entry in your sources. apt-get only reads the sources and install or remove programs.

In order to remove a repository do this:
[LIST]
[*]Open Software Center.
[*]Go to Edit -> Software Sources.
[*]In the new windows that just opened go to the 'Other Software' tab.
[*]The ppas you added will be at the end, and they start with 'http://ppa.launchpad..'
[*]Select the one you need, and press remove.
[*]Close Software Sources.
[/LIST]
Now you can either wait a few seconds on the Software Center so it updates the 'menus', or:

Close the Software Center, go to the terminal and do:
```
$ sudo apt-get autoclean
$ sudo apt-get autoremove
$ sudo apt-get update
```
Then open the Software Center. The extra source should be gone.

I hope it helps,
Regards.

---

### Post by LinTux on 2011-09-30
Sorry papibe.
I figured it without you before you posted.

---

### Post by papibe on 2011-09-30
> **LinTux said:**
> Sorry papibe.
I figured it without you before you posted.
):P  no problem, I'm glad you solved it.
Regards.

---

