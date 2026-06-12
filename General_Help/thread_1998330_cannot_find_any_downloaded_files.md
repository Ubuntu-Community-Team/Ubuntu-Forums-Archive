---
title: "cannot find any downloaded files"
date: 2012-06-06
forum: General Help
---

### Post by linuxman72 on 2012-06-06
whenever i download a file it's files are gone. the program runs fine, but no sign of it can be found. I just recently had to switch from windows but I've only used Linux a few times before.

---

### Post by Linux Al on 2012-06-06
Wich OS and application are you running??

---

### Post by linuxman72 on 2012-06-06
I am using precise (12.04?) and am currently trying to find the files for lugaru

---

### Post by Kr0nZ on 2012-06-06
how are you downloading files? apt-get? wget? browser?

---

### Post by idoitprone on 2012-06-06
> **linuxman72 said:**
> I am using precise (12.04?) and am currently trying to find the files for lugaru

browser download?

```
ctrl+j
``` for firefox

---

### Post by linuxman72 on 2012-06-06
no, this is off the software center
(software center/games/lugaru)

---

### Post by idoitprone on 2012-06-06
> **linuxman72 said:**
> no, this is off the software center
(software center/games/lugaru)

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)


```
dpkg -L lugaru
```

or use the synaptic package manger

first install it
```
sudo apt-get install synaptic
```then run it

```
sudo synaptic
```it more advance than sofware center and it easier to query your installed packages
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
to run the game

there a few ways to run it

press
```
alt+f2
```then type in ```
lugaru
```to run

type 

or you can```

lugaru 
```in termianl to run

---

### Post by linuxman72 on 2012-06-06
But then how do i find the program files?

---

### Post by Kr0nZ on 2012-06-06
in a terminal type
```
which lugaru
```

or try with 'locate'
```
sudo updatedb
locate lugaru
```

In Linux programs are stored in a number of places, unlike windows where most are stored in 'program files'

---

### Post by linuxman72 on 2012-06-06
> **Kr0nZ said:**
> in a terminal type
```
which lugaru
```

or try with 'locate'
```
sudo updatedb
locate lugaru
```

In Linux programs are stored in a number of places, unlike windows where most are stored in 'program files'
for instance, if i'm trying to change a setting in the config.txt file (Linux may not even have one) what should i do?

---

### Post by idoitprone on 2012-06-06
> **linuxman72 said:**
> for instance, if i'm trying to change a setting in the config.txt file (Linux may not even have one) what should i do?

it should be by user to user basis

which mean the config file should be in your home dir
/home/user/

it should be a hidden . file

so it will be located at
/home/user/.lugaru

the setting should all be there

---

### Post by Viper1987 on 2012-06-06
You want to make sure to show hidden files when looking for your config files. You will then see a whole bunch of config files and folders in your home folder

not on my ubuntu pc, but i believe you can press ctrl+h to do so... 

You can also go to View -> Show hidden files

---

### Post by linuxman72 on 2012-06-06
ctrl+h worked. thanks. now i can beat up anthropomorphic rabbits with ease.(mwaa ha ha)

---

### Post by Viper1987 on 2012-06-06
If you're coming from windows, this will take some getting used to. You will not get an install file then run that exe file to extract all of your folders to the proper program files folders. 

Ubuntu Software Center will automatically install everything on your pc in the proper locations....

so the bin folder will have the executable files... and the home folder will have the config files for those executable files

That is a very basic description... I haven't taken any linux classes or anything, but i get by with these forums

---

### Post by Viper1987 on 2012-06-06
try going to the dash and typing "downloads"

---

### Post by Kr0nZ on 2012-06-06
from the man page
```
man lugaru
```
> lugaru  reads  its  configuration  from  $HOME/.lugaru/Data/config.txt,  Which  is  generated  on first launch of the game. The file
       /usr/share/games/lugaru/Data/config.txt (if present) serves as a static default in case no configuration file has yet been generated
       by the user.
so you need to store settings in '.lugaru/Data/config.txt' in your home directory.

---

