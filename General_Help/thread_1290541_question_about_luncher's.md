---
title: "question about luncher's"
date: 2009-10-13
forum: General Help
---

### Post by linux-_- on 2009-10-13
hi every one

i have install [COLOR=Red]freecol[/COLOR] game

and if i want run it i should go to the [COLOR=Red]game folder[/COLOR] by Terminal like this

[php]cd /home/***/freecol[/php]
then

i should Write 

[php]./freecol[/php]so my question is 

can i make luncher on desktop make all that's steps

thanks

---

### Post by DonkeyDragon on 2009-10-13
Try this:


Add a launcher with this command:
/home/***/freecol/freecol

Alternatively some of the better ubuntu gurus will tell you to use chmod, I'm a bit rusty on that however. With chmod it'll be possible to make a launcher that with the command "freecol"

But the other thing should work aswell :)

---

### Post by linux-_- on 2009-10-13
> Try this:


Add a launcher with this command:
/home/***/freecol/freecol

not work :(

---

### Post by ajgreeny on 2009-10-13
Have a look at the properties of the freecol file in the freecol folder in your home folder by right clicking in nautilus.  If the file is not executable, as shown in the permissions tab, select the executable box and close the dialog.  Now make a new launcher on your desktop with the same command you just tried unsuccessfully, and it should work this time.

---

### Post by sisco311 on 2009-10-13
I would move the game in /opt.

```
sudo mv ~/freecol /opt
```
```
sudo chown -R root\: /opt/freecol
```

then create a bash script:
```
gksu gedit /usr/local/bin/freecol
```
copy and past this in the file:
```
#!/bin/bash
cd /opt/freecol
./freecol

```
save it and close the file.

make it executable:
```
sudo chmod +x /usr/local/bin/freecol
```

create a launcher with the *freecol* command.

---

### Post by linux-_- on 2009-10-13
> Have a look at the properties of the freecol file in the freecol folder in your home folder by right clicking in nautilus. If the file is not executable, as shown in the permissions tab, select the executable box and close the dialog. Now make a new launcher on your desktop with the same command you just tried unsuccessfully, and it should work this time.

it was work before , and it's executable

but how to make luncher use this commend at desktop 
./freecol

that my question

---

### Post by linux-_- on 2009-10-13
> I would move the game in /opt.

     Code:
     sudo mv ~/freecol /opt 
     Code:
     sudo chown -R root\: /opt/freecol 
then create a bash script:
     Code:
     gksu gedit /usr/local/bin/freecol 
copy and past this in the file:
     Code:
     #!/bin/bash
cd /opt/freecol
./freecol 
save it and close the file.

make it executable:
     Code:
     sudo chmod +x /usr/local/bin/freecol 
create a launcher with the *freecol* command.
                                                                                               __________________
                

thanks man

it is work  :guitar::guitar::guitar:

---

