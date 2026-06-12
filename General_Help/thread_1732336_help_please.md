---
title: "help please"
date: 2011-04-18
forum: General Help
---

### Post by wizz180 on 2011-04-18
hi i am new to the ubuntu way and i hav a problem using my xbox 360 controller i cant seem to figure it out can any one help me  
this is what i hav done so far: 
[LIST]
[*]sudo add-apt-repository ppa:grumbel/ppa
sudo apt-get update
sudo apt-get install xboxdrv sudo apt-get install xboxdrv-stable
[*][[IMG]http://external.ak.fbcdn.net/safe_image.php?d=80f365d16eb8d6f6aeb8f69269cd29d1&w=90&h=90&url=http%3A%2F%2Fpingus.seul.org%2F%7Egrumbel%2Fxboxdrv%2Fxbox360.png[/IMG]]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")**[Userspace Xbox/Xbox360 USB Gamepad Driver for Linux]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")** 
pingus.seul.orgThis  is a Xbox/Xbox360 gamepad driver for Linux that works           in  userspace. It is an alternative to the xpad kernel driver           and  has support for Xbox1 gamepads, Xbox360 USB gamepads and            Xbox360 wireless gamepads, both first and third party. The            Xbox360 guitar and s



Amend the third line and put in sudo's as follows
[/LIST]

sudo add-apt-repository ppa:grumbel/ppa

Let it run

sudo apt-get update

Let it update

sudo apt-get install xboxdrv-stable

Install the drivers 

On a side note! If you wanted the latest version of the drivers replace the word "stable" with the word "latest"

Which becomes

sudo apt-get install xboxdrv-stable

BUT  BE WARNED !!!!!!! The latest is new and not fully tested and so can  have serious bugs within its coding that might wreck your  computer  entirely!

i am not sure weather this i right of wrong but this is what i was told to do lol :D 

if anyone can help this would be a big help thank you

wizz180

---

### Post by earthpigg on 2011-04-18
link to what told you to do this stuff?

---

### Post by wizz180 on 2011-04-18
the userspace xbox (above was the only link i was given

---

