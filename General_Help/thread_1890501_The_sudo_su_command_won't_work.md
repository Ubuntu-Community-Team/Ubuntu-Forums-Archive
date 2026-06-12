---
title: "The sudo su command won't work"
date: 2011-12-03
forum: General Help
---

### Post by eltiti55555 on 2011-12-03
I was writing a script in my computer for class and I don't know what I did, but when I try to run the "sudo su" command I get "/bin: /bin: is a directory" Please look at this: 
[http://postimage.org/image/bzlnp8fet/full/]("http://postimage.org/image/bzlnp8fet/full/")

Also when I try to edit something using the *sudo * command it says that my password is invalid, i tried changing the shells of one of my users and I got 
*chsh: PAM authentication failed*

---

### Post by MG&amp;TL on 2011-12-03
Don't use:

```
sudo su
```

in Ubuntu, (although some distros will do it)

just prefix any command requiring root access with 

```
sudo
```

See here for more information: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by eltiti55555 on 2011-12-03
> **MG&TL said:**
> Don't use:

```
sudo su
```

in Ubuntu, (although some distros will do it)

just prefix any command requiring root access with 

```
sudo
```

See here for more information: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I have used ```
sudo su 
``` up to now with no problems,the problems is that if I type ```
su
``` into the command line, followed by my password I get an authentication failure. :confused:

---

### Post by MG&amp;TL on 2011-12-03
Please read the link I gave you again.

*sudo* is the **preferred and encouraged** method in Ubuntu, as such discussion of other methods of root access are discouraged in this forum.

It's possible that you have forgotten your password, and that you need to reset it with the command given in the link.

PLEASE, however, use *sudo*-Additionally, people are more likely to give you help in this forum.

---

### Post by fmmarzoa on 2011-12-03
Hi,

Being rude does not help anyone. Neither Answering with a different point than the one asked.

I use sudo <command> most of the time. But I find useful to do 'sudo su' when I need to execute serveral commands that needs root priviledges, or some of them needs to redirect its output to a directory in which regular user has not write permission.

Please, remeber: Recomendation != Divine Law

Regards,

---

### Post by fmmarzoa on 2011-12-03
eltiti55555,

Probably you have overwriten sudo command, added an alias, or something similar. It simply seems like you weren't running sudo...

Try this:

/usr/bin/sudo /bin/su

BTW, you cannot do 'su' by default on Ubuntu without using sudo, even if you're using your right password. To change this behaviour, that's not recommended, you'll need root permissions, and if you cannot do sudo, you'll not be able to gain them, so...

---

### Post by matt_symes on 2011-12-03
Hi

Please post the output of

```
grep root /etc/passwd
```

Kind regards

---

### Post by MG&amp;TL on 2011-12-03
> **fmmarzoa said:**
> Hi,

Being rude does not help anyone. Neither Answering with a different point than the one asked.

I use sudo <command> most of the time. But I find useful to do 'sudo su' when I need to execute serveral commands that needs root priviledges, or some of them needs to redirect its output to a directory in which regular user has not write permission.

Please, remeber: Recomendation != Divine Law

Regards,

Apologies if I appeared rude. I do not recall at any point intending to be. :)

Useful in a 'live' shell, yes, but not in a script.

With due respect to the OP, su and sudo are used by thousands, if not millions of *nix users everyday, if something like this happened regularly, it would be a disaster and *nix would be an insecure wreck. I therefore imagine that the most likely explanation for an incorrect pass is that a needed file in the privilege system got deleted, or that the OP forgot his or her password. It happens to all of us, (I have forgotten mine on several occasions).

Again, apologies if I have given the OP a bad impression of me and/or the forum in general.

---

### Post by matt_symes on 2011-12-03
Hi

Dont worry MG&TL. You advice was fine and very well meaning; just not what the poster wanted.

Take a look at this.
```

matthew@matthew-Aspire-7540:~$ grep root /etc/passwd
root:x:0:0:root:/root:/bin/bash
matthew@matthew-Aspire-7540:~$ sudo su
root@matthew-Aspire-7540:/home/matthew# exit
exit
matthew@matthew-Aspire-7540:~$ sudo sed -i 's/root:x:0:0:root:\/root:\/bin\/bash/root:x:0:0:root:\/root:\/bin/g' /etc/passwd
matthew@matthew-Aspire-7540:~$ grep root /etc/passwd
root:x:0:0:root:/root:/bin
matthew@matthew-Aspire-7540:~$ sudo su
/bin: /bin: is a directory
matthew@matthew-Aspire-7540:~$ sudo sed -i 's/root:x:0:0:root:\/root:\/bin/root:x:0:0:root:\/root:\/bin\/bash/g' /etc/passwd
matthew@matthew-Aspire-7540:~$ grep root /etc/passwd
root:x:0:0:root:/root:/bin/bash
matthew@matthew-Aspire-7540:~$ sudo su
root@matthew-Aspire-7540:/home/matthew# exit
exit
matthew@matthew-Aspire-7540:~$
```This may be the cause of your problem OP.

Kind regards

---

### Post by MG&amp;TL on 2011-12-03
Thanks, Matt. :)

On a side note, OP, while you might need "sudo su", "sudo -i", "sudo bash" etc while running a script 'live', if you have a script written down, it might be easier to:

```

gedit myscript.sh (NOT putting root stuff in)
**sudo** bash myscript.sh
```

Hence raising the script to root, and negating a need to put ANY of the permission guys in.

---

