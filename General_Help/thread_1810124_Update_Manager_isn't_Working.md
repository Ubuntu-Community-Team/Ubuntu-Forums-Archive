---
title: "Update Manager isn't Working"
date: 2011-07-22
forum: General Help
---

### Post by Dunny Pollet on 2011-07-22
I'm hoping people might be able to explain the below error message. I have no idea what it means, except that Update Manager, Synaptic and Software Centre are all broken. It's been like this for a month now, and I'm hoping that this is solvable without me having to re-install the OS.

Thank you for reading this message.

-------------------------------------------------


Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by sikander3786 on 2011-07-22
Welcome to the forums :)

Probably, there is an issue with the lists files. Go to Applications > Accessories > Terminal in Gnome or search the Dash by pressing the <Super> key if you are using Unity. Then run these commands:

```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

Wait for the commands to complete and then run Update Manager again. Let us know how that goes.

---

### Post by Dunny Pollet on 2011-07-22
I got a weird error message when I typed in the first commands, but happily Terminal has paste functions, so I pasted the above into it. The whole thing has worked on Update Manager like a charm. Thanks for the help, and thanks for the welcome. 

Now to try and get the other issues resolved...

---

### Post by sikander3786 on 2011-07-22
You are Welcome :)

You can now mark this thread 'Solved' by using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

You can create new threads for your other problems ;)

Happy Ubuntu-ing!

---

### Post by Dunny Pollet on 2011-07-22
I've copied and pasted the help, for future reference.

Thanks for the info about the "Mark as Solved," Newbie-ness has it's limitations. :)

As for the other issues, I'm waiting until the hundreds of megabytes of package updates has been downloaded and installed. It might be the answer is waiting installation.

Again, thanks for the help. :)

---

