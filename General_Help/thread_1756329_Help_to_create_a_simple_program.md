---
title: "Help to create a simple? program"
date: 2011-05-12
forum: General Help
---

### Post by cjsa on 2011-05-12
So, I'm a noob, if even that, and I need someone to help me create a little program or something like that.

I need a program that automaticly runs this command in the terminal when I use it:
sudo modprobe nvidia_g210m_acpi

Sure, I know that it's not that hard to just write it in terminal and so on, but I really want a program for it :)
oh, and I'm using ubuntu 11.04 if U need to know that?

I would be really thankful if someone could help me with this! :)

---

### Post by Lars Noodén on 2011-05-12
> **cjsa said:**
> So, I'm a noob, if even that, and I need someone to help me create a little program or something like that.

I need a program that automaticly runs this command in the terminal when I use it:
sudo modprobe nvidia_g210m_acpi

Sure, I know that it's not that hard to just write it in terminal and so on, but I really want a program for it :)
oh, and I'm using ubuntu 11.04 if U need to know that?

I would be really thankful if someone could help me with this! :)

All you need is a shell script or an alias.  Below is how you would do it for a shell script:

```

#!/bin/sh

/usr/bin/sudo /sbin/modprobe nvidia_g210m_acpi

```

You can then make that file executable by changing the permissions.

```

chmod +x myscript.sh

```

---

### Post by anaconda on 2011-05-12
I would recommend using gksudo instead of just sudo.

gksudo asks the password using a graphical interface. Sudo:s password prompt may not come visible, if you launch the script from a graphical launcher.

And you dont have to give paths in the script.. You can, but dont have to.  /usr/bin and /sbin are on the path anyway...

---

### Post by Lars Noodén on 2011-05-12
> **anaconda said:**
> I would recommend using gksudo instead of just sudo.

gksudo asks the password using a graphical interface. Sudo:s password prompt may not come visible, if you launch the script from a graphical launcher.

And you dont have to give paths in the script.. You can, but dont have to.  /usr/bin and /sbin are on the path anyway...

Right.  /usr/bin and /sbin are on the *default* path.  

However, with scripts it's a Very Good idea to explicitly set the path either with the variable $PATH or by spelling it out for each program because there is no telling where or how they will run.  If one wants to really do things right one ought to set the [Internal Field Separator](http://www.livefirelabs.com/unix_tip_trick_shell_script/oct_2003/10132003.htm) ( $IFS ), too.

So an alternate way of doing the script would be 

```

#!/bin/sh
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

sudo modprobe nvidia_g210m_acpi

```

---

### Post by cjsa on 2011-05-12
Thanks for the answers!!

But I'm having a problem, and it might be because i don't really know what I'm doing ^^ :)
I can't get it to work :S I tried to write the code in the terminal but nothing...

maybe one of you could make a step by step thingy? that would really be gold!!

---

### Post by Lars Noodén on 2011-05-12
> **cjsa said:**
> 
maybe one of you could make a step by step thingy? that would really be gold!!


1. enter these in the terminal:

```

touch myscript.sh;    # create the file
chmod +x myscript.sh; # make it executable

```

2. open the file with nano, geany, kate or your favorite text editor

3. put the following in it:

```

#!/bin/sh
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

sudo modprobe nvidia_g210m_acpi

```

4. done! you can run it 
```

./myscript.sh

```

---

### Post by nothingspecial on 2011-05-12
This is going to create an alias for you. Do the lines one by one.

```
echo 'alias nv="sudo modprobe nvidia_g210m_acpi"'  | tee -a ~/.bashrc
```

```
. ~/.bashrc
```

Just copy and paste them.

Now, to run that command, from now on all you have to do is open a terminal and type nv.

By the way, do you only need to load this module occassionaly or would you like it to load every time you boot. Because if you do.

Type ```
echo  nvidia_g210m_acpi | sudo tee -a /etc/modules
``` and it will :D

And in that case you don't need to do the first bit.

---

### Post by cjsa on 2011-05-12
Thank you Lars!! It works great!


Thanks for all the help and answers dudes!

---

### Post by Lars Noodén on 2011-05-12
You're welcome.  

Once you've got it running the way you like it, you can give it a good home by moving it to [/usr/local/sbin](http://manpages.ubuntu.com/manpages/natty/en/man7/hier.7.html)

---

