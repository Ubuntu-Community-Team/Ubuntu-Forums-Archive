---
title: "Unable to run shell script"
date: 2011-01-12
forum: General Help
---

### Post by shanks. on 2011-01-12
i have a shell script at the following location

/media/1E30D23B30D2199B/matu20Xa/update/install/main.sh

when i try to run it as ./main.sh 

it returns the  reply

```
 bash: ./main.sh: Permission denied

```i am logged in a root

still i am facing this problem

i have tried doing chmod +x and also chmod u+x but in vain

anyone help please

---

### Post by shanks. on 2011-01-12
someone help please :(

---

### Post by ankspo71 on 2011-01-12
Hi,

> i am logged in a root
Do you mean you are logged into a terminal as root?

Is the file owned by "you" or "root" if you right click on it and check the permissions? Have you tried running the script with "sudo" yet? 
```
sudo /media/1E30D23B30D2199B/matu20Xa/update/install/main.sh
```

I think 'chown' might be better than using 'chmod u' for setting user permissions:
[sudo chown userid:groupid /path/to/file]
```

sudo chown shanks:shanks /media/1E30D23B30D2199B/matu20Xa/update/install/main.sh
OR
sudo chown 1000:1000 /media/1E30D23B30D2199B/matu20Xa/update/install/main.sh
(assuming you are user 1000)
```
Now try executing the script again.

PS. Here are more details about chmod and chown for Ubuntu.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

PSS You might have to run the script with "sh" if "bash" doesn't understand it. I ran into that problem a couple of times. 
```
sh /media/1E30D23B30D2199B/matu20Xa/update/install/main.sh
```

Hope this helps.

---

### Post by DaithiF on 2011-01-12
my guess is that this is a vfat or ntfs filesystem and since 10.04 these are mounted with a 'showexec' option which means that text files are not executable.

just run it using bash or sh instead.

```
bash /path/to/your/file

```or
```
sh /path/to/your/file
```

---

### Post by ankspo71 on 2011-01-12
> **DaithiF said:**
> my guess is that this is a vfat or ntfs filesystem and since 10.04 these are mounted with a 'showexec' option which means that text files are not executable.

just run it using bash or sh instead.

Yep, thanks for mentioning that. I just tried a script of my own on my second drive (formatted in xfs) and it didn't work either:
```
sudo /media/sdb7/kubuntu-packages
[sudo] password for james: 
sudo: unable to execute /media/sdb7/kubuntu-packages: Permission denied
```
'sudo bash' and 'sudo sh' worked like a charm. (my particular script calls for sudo to install packages)

---

### Post by shanks. on 2011-01-12
when i said i was logged in as root, what i meant was that i was logged in as user `root`

and not form the terminal

and guys i have tried all the options of bash, sh u have given above

still i get same reply


bash: ./main.sh: Permission denied

---

### Post by shanks. on 2011-01-12
even when i right click on properties and then try to change the permissions, event hat does not seem to be possible

as i am not  able to change the permissions there at all

---

### Post by shanks. on 2011-01-13
no one? :(

---

### Post by amsterdamharu on 2011-01-13
If you type 
```
bash myfile
```

It doesn't matter what the rights on the file are, as long as you can read it you can execute it.

The reason why you can't execute it like
```
./myfile
```
might be given in a previous post:
> my guess is that this is a vfat or ntfs filesystem and since 10.04 these  are mounted with a 'showexec' option which means that text files are  not executable.

---

### Post by probono on 2011-01-15
Here is a somewhat hackish way to patch away the "showexec" option from the automounter:

```
sudo sed -i -e 's|showexec|\x00\x00\x00\x00\x00\x00\x00\x00|g' /usr/lib/udisks/udisks-daemon
```

CAUTION: Works for me after a reboot, but no guarantees. Make a backup before you do this!

---

### Post by redfern314 on 2011-04-15
> **probono said:**
> Here is a somewhat hackish way to patch away the "showexec" option from the automounter:

```
sudo sed -i -e 's|showexec|\x00\x00\x00\x00\x00\x00\x00\x00|g' /usr/lib/udisks/udisks-daemon
```

CAUTION: Works for me after a reboot, but no guarantees. Make a backup before you do this!

This worked perfectly for me. Thanks so much!

However, I would very much appreciate it if someone could explain what exactly this code does and how it works - just for learning purposes.

Thanks :D

---

### Post by Vaphell on 2011-04-15
in a given file it replaces 'showexec' with null characters \x00
**sed** manipulates text
**-i** = in place (modify input file(s) given at the end)
**-e** = next parameter will desribe operation to perform
**'s[SOME_CHAR]pattern[SOME_CHAR]replacement[SOME_CHAR]g'** = (s)ubstitute all (g)roups matching to pattern with replacement, separator of that expression is taken from the first position after s ('s/a/b/g' and 's:a:b:g' do the same thing)
**sudo** = grants temporary admin rights because the file belongs to system and ordinary user can't touch it.

---

### Post by idokus on 2011-05-04
From what I understood while searching for this fix
[http://ubuntuforums.org/archive/index.php/t-1606193.html](http://ubuntuforums.org/archive/index.php/t-1606193.html) 

udisks changed its behaviour to set "showexec" in order to disable that normal text files are shown as executables. (I've also seen it as part of security so you can't execute files from mounted devices, if person A leaves a usb (or similar) person B logged in under different credentials is able to execute the usb's files, and thus create a possible security leak as it runs under the same rights as person B.)

Enough side track on reasons why you might want it.

What the command actually does is it replaces the string "showexec" with null character, carefully not changing the number of characters.

Basically this is a hack to save the trouble of recompiling the mount daemon. As discribed in the link above.

Although I think this should be an option. it might be an option in /etc/avahi/services/udisks.service (but i couldn't find the documentation, but it's the only file mentioning udisk under /etc (the system wide configuration directory)

---

### Post by ravipfiles on 2011-05-22
Thanks Probono,
I was googling from many days to find a way to get rid off showexec option. your trick did work for me as well. but how did u get to know that showexec option is hidden in /usr/lib/udisks/udisks-daemon file.
and what does this command "sudo sed -i -e 's|showexec|\x00\x00\x00\x00\x00\x00\x00\x00|g' /usr/lib/udisks/udisks-daemon" do ?

---

### Post by idokus on 2011-05-23
> **ravipfiles said:**
> Thanks Probono,
I was googling from many days to find a way to get rid off showexec option. your trick did work for me as well. but how did u get to know that showexec option is hidden in /usr/lib/udisks/udisks-daemon file.
and what does this command "sudo sed -i -e 's|showexec|\x00\x00\x00\x00\x00\x00\x00\x00|g' /usr/lib/udisks/udisks-daemon" do ?

udisks-deamon discovers newly inserted usb's and tries to mount them.

showexec is the option which says that you cannot execute any file on the mounted device

the sed command replaces showexec with the null characters.

---

### Post by probono on 2012-11-23
In the latest versions of Ubuntu, the command is

> sudo sed -i -e 's|showexec|\x00\x00\x00\x00\x00\x00\x00\x00|g' /usr/lib/udisks2/udisksd

This takes effect after
> sudo killall udisksd
sudo /usr/lib/udisks2/udisksd &

---

### Post by wildmanne39 on 2012-11-23
Old thread closed. Thanks for sharing.

---

