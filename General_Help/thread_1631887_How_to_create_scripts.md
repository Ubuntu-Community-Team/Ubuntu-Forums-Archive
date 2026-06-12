---
title: "How to create scripts"
date: 2010-11-27
forum: General Help
---

### Post by Spyderkid on 2010-11-27
I want to be able to create simple scripts from terminal for example to make it say hello, or hopefully leading onto being able to change directories and running a couple of things in terminal from a script like ```
 make clean
make
sudo make install 
``` 

for example. can anyone tell me how?

---

### Post by NertSkull on 2010-11-27
You need to put your commands in a file.  Then save the file and make it executable (use the chmod command).

Then to run it, CD into the directory you saved it in and run it by typing 

./name_of_file.sh

thats the very basics of it.

---

### Post by Spyderkid on 2010-11-27
So shall I use a text editor to create the commands in a file?

---

### Post by Frogs Hair on 2010-11-27
This is helpful. [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Spyderkid on 2010-11-27
Sorry "Frogs Hair" couldn't find anything particulary helpfull.

---

### Post by Frogs Hair on 2010-11-27
> **Spyderkid said:**
> Sorry "Frogs Hair" couldn't find anything particulary helpfull.

Oh, well, I thought the script writing section may useful , I thought you were just beginning. ;)

---

### Post by Spyderkid on 2010-11-27
I've created a new file in my home folder called it wireless-driver and have enabled executing through properties haven't tested it yet have had no need but when I do i'll post to say what happened. what I put in the file was this by the way:

```

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/

cd driver

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/

make clean

make 

sudo make install



```

---

### Post by Vaphell on 2010-11-27
make it 'make clean && make && sudo make install'

&& means that the next part is executed only if previous one was successful (also one can use || to run the command only when the last one failed)

also add so called shebang at the beginning of the file
#!/bin/bash
or
#!/bin/sh
to explicitly define which shell program is to be used to run the script

---

### Post by Spyderkid on 2010-11-27
Is this better?

```

#!/bin/bash

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/

cd driver

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/

make clean && make && sudo make install

```

---

### Post by Spyderkid on 2010-11-27
Also I want to be able to know when the script has finished running...

Because I have ran it and it works but I don't know when it finishes.

Also I want to be able to add these commands to the end of my script ```
sudo modprobe 8712u
echo "8712u" | sudo tee -a /etc/modules 
```

---

### Post by Spyderkid on 2010-11-28
Bump

---

