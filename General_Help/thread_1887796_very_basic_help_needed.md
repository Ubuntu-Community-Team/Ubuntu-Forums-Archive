---
title: "very basic help needed"
date: 2011-11-27
forum: General Help
---

### Post by patriotkiller18 on 2011-11-27
while installing ubuntu, I inadvertently gave my comp the wrong name. I got the user name correct, but I need to change the comp name.      name1@name2---I need to be able to change name1..
I have searched but all I find is methods for changing user names. Any help is appreciated.
Thanks,
patriotkiller18

---

### Post by fantab on 2011-11-27
> **patriotkiller18 said:**
> while installing ubuntu, I inadvertently gave my comp the wrong name. I got the user name correct, but I need to change the comp name.      name1@name2---I need to be able to change name1..
I have searched but all I find is methods for changing user names. Any help is appreciated.
Thanks,
patriotkiller18

You can change this with either **Ubuntu-Tweak-Tool** or with **Ailurus**. I don't know, however, how safe it is to do so. It caused some problems on my desktop using another Distro. 

If it is not too much inconvenience to you then ignore it.

---

### Post by Dangertux on 2011-11-27
> **patriotkiller18 said:**
> while installing ubuntu, I inadvertently gave my comp the wrong name. I got the user name correct, but I need to change the comp name.      name1@name2---I need to be able to change name1..
I have searched but all I find is methods for changing user names. Any help is appreciated.
Thanks,
patriotkiller18

If you look in your /etc/hosts file and edit the following (sudo nano /etc/hosts)

```

127.0.0.1       localhost wronghostname
127.0.1.1       wronghostname

```change it to

```

127.0.0.1     localhost righthostname
127.0.1.1     righthostname

```Your prompt will now be displayed username@righthostname. You'll have to reboot for this to fully take effect.

---

### Post by bluexrider on 2011-11-27
[Dangertux]("http://ubuntuforums.org/member.php?u=1322416") 


He probably shouldn't change the 127.0.0.1 localhost.

The one he wants to edit would be 127.0.1.1 computername.

[SIZE=3][COLOR=Red] name1@name2---I need to be able to change name1..


[/COLOR][/SIZE]

---

### Post by gman16000 on 2011-11-27
i would change two files.

first "sudo vi /etc/hosts" and set to something like this:
```

127.0.0.1   localhost newhostname
127.0.1.1   newhostname

```

second, "sudo vi /etc/hostname" and put your hostname in that file.

---

### Post by Dangertux on 2011-11-27
> **bluexrider said:**
> [Dangertux]("http://ubuntuforums.org/member.php?u=1322416") 


He probably shouldn't change the 127.0.0.1 localhost.

The one he wants to edit would be 127.0.1.1 computername.

[SIZE=3][COLOR=Red] name1@name2---I need to be able to change name1..


[/COLOR][/SIZE]

They're both localhost

127.anything.anything.anything is all loopback.

So..

You could do

```

127.0.0.1 localhost correcthostname
127.0.1.1 correcthostname #this is a stupid debian hack
127.3.4.5 correcthostname
127.55.24.231 localhost

```and be fine, if you like being redundant.

Also if OP is referring to his prompt it will be in the format of username@hostname or username@fqdn if you assigned one.

---

### Post by bluexrider on 2011-11-27
okay then

---

### Post by Dangertux on 2011-11-27
> **bluexrider said:**
> okay then

Nvm I see what you're saying I didn't type it the same way the first time you can append correcthostname to localhost on 127.0.0.1 entry though it will change what is after the @ not before.

---

### Post by bluexrider on 2011-11-27
That was the point. Thanks for your reply

---

### Post by Dangertux on 2011-11-27
> **bluexrider said:**
> That was the point. Thanks for your reply

Yeah no problem it's late :-(

So wait.. OP did you make the wrong hostname or the wrong username? Because now I'm confused as to which you're wanting changed.

---

### Post by ExileAmongYou on 2011-11-28
> **gman16000 said:**
> i would change two files.

first "sudo vi /etc/hosts" and set to something like this:
```

127.0.0.1   localhost newhostname
127.0.1.1   newhostname

```

second, "sudo vi /etc/hostname" and put your hostname in that file.

Possibly a bit off-topic, but perhaps vi (or nano) is not the best option for someone who's just getting started? It took me quite a while to get comfortable with vi, and it sounds like the OP is fairly new to the terminal and editing the system files.

OP, "gksudo gedit /etc/hosts" might be a better command to try if you want to edit these files.

---

### Post by patriotkiller18 on 2011-11-28
What is OP?

If anyone else has a safe way to make the changes I need, I would really appreciate it; it's important!
*[COLOR=Red]**name1**[/COLOR]*@name2....I need to change[I][B][COLOR=Red] name1....
[COLOR=Black]Let's Keep Trying!!

[/COLOR][/COLOR][/B][/I][COLOR=Red][COLOR=Black]Thanks,[/COLOR][/COLOR][I][B][COLOR=Red][COLOR=Black]
[/COLOR][/COLOR][/B][COLOR=Red][COLOR=Black][/COLOR][/COLOR][/I][COLOR=Red][COLOR=Black]patriotkiller18
[/COLOR][/COLOR]

---

### Post by patriotkiller18 on 2011-11-28
What is OP?

[COLOR=Red]***name1***[/COLOR]@name2    I need to change [COLOR=Red]*name1*[/COLOR]

Thanks,

patriotkiller18

---

### Post by Vaphell on 2011-11-28
OP = original poster

```
gksudo gedit /etc/hosts /etc/hostname
```
change the name, save both files

---

### Post by patriotkiller18 on 2011-11-28
[COLOR=Red]**name1**[/COLOR]@name2    it seems that all this does is change name2. I need to change **[COLOR=Red]name1[/COLOR]**.  I am new to linux so if I am wrong, just say so but that code only gave me the option to change name2. Please reply, it seems like you may be able to help me with this problem.
Thank You,
patriotkiller18

---

### Post by ExileAmongYou on 2011-11-28
> **patriotkiller18 said:**
> [COLOR=Red]**name1**[/COLOR]@name2    it seems that all this does is change name2. I need to change **[COLOR=Red]name1[/COLOR]**.  I am new to linux so if I am wrong, just say so but that code only gave me the option to change name2. Please reply, it seems like you may be able to help me with this problem.
Thank You,
patriotkiller18

Wait, you're talking about how in the terminal, the prompt shows name1@name2? name1 should just be your username, name2 is your computer name. When I open a terminal, I get myname@geekyreferenceichoseasmycomputername. If you've managed to to change name2, you've changed your computer's name. You said you had already found tutorials for chnaging your user name, so maybe you should try those?

---

### Post by haqking on 2011-11-28
if it is a one time thing for the current uptime then you can just

```
hostname <name>
```

If you want persistence then you need to edit one of the system files

```
/etc/hosts
```

as already mentioned but you can also edit the hostname file which is often less confusing

it is in /etc a file called hostname

```
/etc/hostname
```

edit them with editor of choice, vi/vim, nano, gedit (use gksudo and not sudo for grpaphical apps such as gedit

also if it is just your prompt you want to change b ut keep the computer name the same you can make it say what you like with:

```
PS1="what i want my prompt to be : "
```

where the string "what i want my prompt to be : " should contain what you want to see at the prompt.

Cheers

---

### Post by haqking on 2011-11-28
> **patriotkiller18 said:**
> What is OP?

[COLOR=Red]***name1***[/COLOR]@name2    I need to change [COLOR=Red]*name1*[/COLOR]

Thanks,

patriotkiller18

> **patriotkiller18 said:**
> [COLOR=Red]**name1**[/COLOR]@name2    it seems that all this does is change name2. I need to change **[COLOR=Red]name1[/COLOR]**.  I am new to linux so if I am wrong, just say so but that code only gave me the option to change name2. Please reply, it seems like you may be able to help me with this problem.
Thank You,
patriotkiller18

ok so the command in my post above will allow you to change your prompt.

Edit the

/etc/hostname fiel to change your hostname

or do it temporarily with

hostname <name>

if you wish to change the first part of your prompt without using the PS! command above to change your prompt then you need to change your username (login name)

this can be a little troublesome due to home directory and links etc etc.

Often it is easier to just create a new user, if you really need to change your existing suername then as follows:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

where the "old" is your old or current name and "new" is the name you wish it to be.

You can do the commands with ```
sudo
``` or ```
sudo -i
```

this will change the name but i have found issues with the files i mentioned above

```
sudo usermod -c "Real Name" -l New_Username Old_Username
```

However to avoid possible headaches i would either create a new user with the name i wanted, or just change my prompt if it is a prompt issue

---

