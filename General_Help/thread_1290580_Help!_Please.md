---
title: "Help! Please"
date: 2009-10-13
forum: General Help
---

### Post by Carlitoes on 2009-10-13
How to install vlc skin editor? i have downloaded the package which is tar.gz format so what would i need to do to install the app or convert the package? i am a noob so please be nice! :D

---

### Post by TwinStinger on 2009-10-13
Have you unpacked the .gz file?

If not do so and then open up a terminal and navigate to where the extracted files are located.

Then do 
"chmod a+x VLCSkinEditor"     -Makes the file executable

after that  "./VLCSkinEditor"

/ Twinned

Edit: I assume that you have java.

---

### Post by Carlitoes on 2009-10-13
Thanks i cant find how to navigate with the terminal yet! i just right clicked on the file and allowed it to execute  and it works! thanks from the uk.:guitar:

---

### Post by sisco311 on 2009-10-13
[list]

[*]move the .tar.gz to your desktop. 

[*]open a terminal

[*]change the current working directory to ~/Desktop
```
cd ~/Desktop
```

[*]extract the archive to /opt/VLCSkinEditor:
```
sudo mkdir /opt/VLCSkinEditor
```
```
sudo tar -C /opt/VLCSkinEditor/ -xvzf VLCSkinEditor_unix.tar.gz
```

[*]make the VLCSkinEditor file executable:
```
sudo chmod +x /opt/VLCSkinEditor/VLCSkinEditor
```

[*]create a bash script:
```
gksudo gedit /usr/local/bin/VLCSkinEditor
```

[*]copy/paste this in the file:
```
#!/bin/bash
cd /opt/VLCSkinEditor
./VLCSkinEditor

```save the file and close it

[*]make it executable:
```
sudo chmod +x /usr/local/bin/VLCSkinEditor
``` 

[*]install the dependencies:
```
sudo apt-get install openjdk-6-jre
``` 

[*]create a launcher on your desktop or panel, type VLCSkinEditor in the command filed.

[/list]

NOTE0: linux is case sensitive (copy/paste the commands line by line in your terminal)
NOTE1: there is no visual feedback when you type your password, just type it and press enter.

---

