---
title: "Kate doesnt respect option of opening documents in tabs"
date: 2009-10-22
forum: General Help
---

### Post by dumblebee100 on 2009-10-22
well Im using karmic koala beta ( and some upgrades till some days back )

I installed kubuntu desktop and dependent packages to get kde 4.3 up and running

after some days of using it I find annoying that kate doesnt save its settings and I have to use a no_doc session to get a session to open kate with empty document and with all settings saved ..well this is solved in latest updates I think so ..now it remembers settings so I dont use profile now ..

but my problem is when I selected 3 documents ( all of text ) and then press ENTER then kate opens 3 seperate windows but when I open with right click and select open with kate then it opens kate with tabs of three documents ..

for your information ..I edited kate command in menu editor 
to kate -geometry 750x550-210-100 %U 
it  works and opens 3 windows of kate which I dont want ..
so deleted all the extra command and kept it as usual but still I dont want different windows of kate ..I want tabs .

before adding geometry I didnt tried opening 3 docuents in kate by pressing ENTER ..so I dont know ..
does anyone faces problem like me ?

---

### Post by Giblet5 on 2009-10-22
> I didnt tried opening 3 docuents in kate by pressing ENTER

...by pressing ENTER. I sense there's more to it than that...

Do you mean that you try to open three files in kate from a command line, like ```
kate file1.cpp file2.cpp file3.cpp
``` and that opens three kate windows?

On this box, that does bad things.

If kate isn't saving its settings, it's probably a permissions problem under ~/.kde...

```
sudo find ~/.kde -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find ~/.kde -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

will fix that.

---

### Post by dumblebee100 on 2009-10-22
thanks for the reply 

my problem is not what you thought ..well I will explain it more clearly to you 

I went to this directory /home/sam/.kde/share/config
then there are many config files and for kate testing purpose I choosed this directory
I use dolphin file manager

I selected some 3 files in it by mouse and then pressed ENTER then kate opens 3 kate windows ..but I wish that they all open in a single window but with different tabs as in gedit ( gedit works fine and I want kate to work fine too )

I didnt opened from terminal 
as far as kate settings go ...now the settings are saved ..may be the updates part solved it

---

### Post by dumblebee100 on 2009-12-14
well I solved this problem I think so 

the solution is 
goto kcontrol>advanced>file associations>
search text/plain
then edit the kate properties for command as
kate -u %U
here -u is to use the already using kate instance if possible and
%U is the url of the document being opened

---

