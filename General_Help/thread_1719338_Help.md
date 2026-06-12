---
title: "Help"
date: 2011-04-01
forum: General Help
---

### Post by Timo908 on 2011-04-01
I'm trying to download my latest Java for my comp. And when I do the sudo command, I get the following message
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.' 

Anyone Have any idea what to do?

---

### Post by Diametric on 2011-04-01
Could you post what command you used to run the java update?  Meaning, did you use the terminal, or did you use Synaptic.  Also, what version of Ubuntu are you running.  A little more info would be helpful.

---

### Post by Timo908 on 2011-04-01
I was trying to update my whole system I have ubuntu 10.04 and it says the same thing for when I try to update java in the terminal.
[[IMG]http://img33.imageshack.us/img33/6978/helplol.png[/IMG]](http://img33.imageshack.us/i/helplol.png/)

---

### Post by sanguinoso on 2011-04-01
Can you tell us what is on line 54 in that file?
```
gedit /etc/apt/sources.list
```
Then scroll to line 54 and copy & paste it here. What the error is telling you is that there is an error in that file. The sources.list file tells apt-get where to download packages from. More info on that file here [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Timo908 on 2011-04-01
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner

---

### Post by sanguinoso on 2011-04-01
Which ubuntu version are you running? The similar line from my install is ```
deb http://archive.canonical.com/ubuntu lucid partner
``` As you can see yours is missing the name part which in my case is lucid, for 10.04. You can find your version number and name in the menu, System -> About Ubuntu. Then type ```
sudo gedit /etc/apt/sources.list
``` And put the name from your version in that file using the line from mine as a reference. And then you can re-run the commands you tried above.

---

### Post by Timo908 on 2011-04-01
As said in my post with the picture: 10.04

---

### Post by sanguinoso on 2011-04-01
So you can therefore just replace your line 54 with the one I pasted previously and re-run the commands that you were trying to install java with.

---

### Post by Timo908 on 2011-04-01
thanks for the help. I got it to work :)

---

### Post by sanguinoso on 2011-04-01
Not a problem, if you could mark the thread as solved that would be great. Its under Thread Tools -> Mark this thread as solved

---

