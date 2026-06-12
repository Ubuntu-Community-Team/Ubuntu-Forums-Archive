---
title: "HALP. Seriously. I ISO'd a backup of my haywired ubuntu USB, now how do I restore it?"
date: 2011-05-28
forum: General Help
---

### Post by Baniita on 2011-05-28
I'm pretty darn sure no one else has this problem. **I'm sick of re-installing everything every single time. **ARGH. **I talk a lot, so I bolded the stuff you shouldn't skim over.**

Who else but me could bork 4 USBs over the span of 2 1/2 weeks? Well, that's what I get for walking around with a plugged-in USB poking out of my bag. (I couldn't help it, okay! And I was being as careful as I could, but I can't stop my bad luck and idiots running into me. Honestly, my luck is abysmal.)
[B]
Anyway, before my USB went haywire on me, I made a copy of everything on it in the form of an ISO, because I have no clue what I'm doing. (I mean, it does SOMETHING, doesn't it?)[/B]
I had installed a whole bunch of stuff, including wine, winetricks, desmume, etcetc... I've had to re-install everything 6 times already. THAT'S NOT AN EXAGGERATION. Not only do I really not want to re-install everything I need, I don't always have the internet connection. I only get a limited time here at Starbucks.
[B]
Putting the ISO by click-and-drag obviously wouldn't work. I've tried simply moving the files from the ISO onto the USB, but there are these files that ubuntu won't let me copy. Isn't there some way I can restore all my files and programs without going through the long process?[/B]

I'm like, programming and ubuntu illiterate, so please help me out here? /Bowbow.

---

### Post by Thewhistlingwind on 2011-05-28
df to get where your flash is mounted

sudo  dd if= (Your iso) of= /dev/(Your flash drive)

If you put in the wrong drive, it completely destroys your install.

Have fun.:D

EDIT: This will destroy all data on the target device. DON'T use it on a drive with stuff you need/haven't backed up.
EDIT2: DD reads data and copies it somewhere else. if= is your source file (or drive) of= is your target. You can also use this for making forensic disk images.

---

### Post by Baniita on 2011-05-28
Hommmggggffff. Thank yooou. I'm a bit occupied at the moment, but I'll definitely give that a try. :3

Hopefully, it'll work.

---

### Post by lmn. on 2011-05-28
I'll read it all because you told me not to.

when I 1st moved over to ubuntu for good (not too long ago) I was reinstalling daily. so much fun. in the end you can replicate your config in 10 minutes as opposed to the couple of hours it takes originally.

I didn't mind at all, a refreshing contrast to the boring, consistent style of windows... nothing ever goes wrong and you'l end up doing the same thing in the same way, over and over and **over** again.

best bet to keep your backed-up files and the install cd separate.
better yet, use a flash drive and stop wasting disks.

---

### Post by Baniita on 2011-05-28
Arrgghh... I've tried it twice. It didn't work either times. When I looked at the finished copy, the file names all come out as gibberish (rectangles with squigglies in them) and isn't anything like it's supposed to be. D8 

Anything else I can try, anyone?

---

### Post by Thewhistlingwind on 2011-05-28
Reboot, then they'll be there, promise.

---

### Post by Baniita on 2011-05-28
@Imn: Lololol. You obviously didn't read it all. XD It's apparent that I'm using USBs. I borked like, four, remember? 

I'm using ubuntu liveCD right now. It's not rewritable, but I usually use rewritables.

---

### Post by Baniita on 2011-05-28
I did reboot. /Scratches head.

; v;" It said it wasn't bootable.

So I suppose there's something wrong with the data on my ISO? (It doesn't seem so, though. Everything looks fine.)

---

### Post by Thewhistlingwind on 2011-05-28
> **Baniita said:**
> I did reboot. /Scratches head.

; v;" It said it wasn't bootable.

Don't boot into it.

---

### Post by Baniita on 2011-05-28
Ehhhh? D8" /Bashes head. I'm sorrrryyy. But I don't even know what that meaaans. ; v;

Stupid question, how do I work it without booting the USB? 8D"

---

### Post by lmn. on 2011-05-28
ok so I didn't read it properly, I told myself I did though, and that;s all that counts.
also it's an L ol

---

### Post by Thewhistlingwind on 2011-05-28
> **Baniita said:**
> Ehhhh? D8" /Bashes head. I'm sorrrryyy. But I don't even know what that meaaans. ; v;

Stupid question, how do I work it without booting the USB? 8D"

The point was to get usable files after ubuntu boots it so that you can restart AGAIN then boot it.

You could also try the conv and output flags.

---

### Post by linuxinstalledfromhdd on 2011-05-28
It would be nice to know what you used to back it up with? Remastersys? What?

---

### Post by chah on 2011-05-28
Hi Banita,

First you should check that the iso is ok, cause if it isn't we can't help you. I'm not sure where you stored the .iso. Is it on an external HDD? The method I'm going to outline uses the command line, not the GUI. You need to know or learn a little bit about paths and directory structure to complete it using this method.

Let me assume your iso file is stored on /dev/sda1, and /dev/sda1 is mounted on /media/sda1. So in this example, the filename of your iso would be /media/sda1/USB_backup.iso. Replace this with the correct path to your iso in the examples below.

To check the status of the iso, you need to mount it somewhere then go poke around in the mounted system to make sure all the files you expect to be in the iso, really are in the iso:
```

cd              # Change to your home directory
mkdir tempMount # Make a temp directory for mounting the iso
sudo mount -o loop /media/sda1/USB_backup.iso tempMount # mount your iso file at the temp directory.
cd tempMount
ls -la          # Make sure the files in your iso are ok

```
You'll need to enter your password at any line with sudo, which executes the command with root priviledges. At this point you should poke around in tempMount to make sure your files are all right. If this step doesn't work, the rest of the stuff below won't work either. After you've confirmed that your files are there, unmount it again:
```

cd
sudo umount tempMount

```

To restore the iso, you need to an empty USB of the same size as the one that you backed up. This USB will be overwritten by the backed-up ISO. When you insert it, Ubuntu will likely auto-mount it. Unmount it from the file-manager window by clicking on the eject icon. Now you need to know the name ubuntu assigns to your USB. Use the fdisk command:
```

sudo fdisk -l

```
This will give you an overview of all storage devices that ubuntu can find on your system. You need to locate the new USB drive from among these. Don't get this part wrong, because the next step is going to overwrite the storage device you choose. You should also check that the size of your iso file, is the same as the size of the USB device you are trying to restore it to. I'll assume your device is /dev/sdx which is most likely not a real device on your system, but you should replace it with the name of the device that you found with the fdisk command above. If should be something like /dev/sdb or /dev/sdc

Now comes the dangerous part: copying the iso back onto your destination device. You need to be careful you get the destination correct, because it is all too easy to wipe off your internal drive by typing /dev/sda instead of /dev/sdb for example and lose all your data. Be very careful here, you have been warned. 
```

sudo dd if=/media/sda1/USB_backup.iso of=/dev/sdx

```
This command copies, byte-for-byte, the contents of USB_backup.iso to the device that ubuntu identifies as /dev/sdx, that you found above using the fdisk. This command will take a long time to complete, could be an hour or more depending on your transfer rates and size of the device you're restoring. I can't overemphasize how careful you need to be before pressing enter to this command. When I do this for big restorations, I sometimes like to check to make sure that it is restoring appropriately and get an update of the progress. The below commands are not necessary, but can be reassuring to know things are proceeding. You can skip it if you don't feel comfortable.

The dd command can receive a signal that will cause it to dump it's progress status, if you give it the appropriate signal. To give the signal you use the kill command, but the kill command needs to know the process id (PID) to send the signal to. Leave the dd command running in one terminal window, and open a second window and type:
```

pgrep -lf dd

```

pgrep will find and report the PID's for processes with dd in the name. It is likely that there will be more than 1 such process, you need to locate the process and get the ID for the dd command you executed above, which should be an integer greater than zero. Once you have this number you send a signal to dd that will ask it to tell you its progress status with the kill command:
```

kill -USR1 PID

```
where PID is the ID you found above with pgrep command. Now go back to the window where dd is still running. You'll see some information appeared on the screen that will tell you how much it has copied, and how fast it is going. You can get an estimate of how long it's going to take.

When the dd command is finished, you should have the contents of the backup.iso restored onto the USB device. If your USB was bootable before, you should shut down and be able to reboot your computer from your restored device.

---

### Post by Baniita on 2011-05-31
***@ch'yeah!! - YOU, SIR--ARE INCOMPREHENSIBLY AMAZINGREAT.***
Fffff, seriously. Finally, at least a step forward. I really thought  it'd really work completely this time, but unfortunately it didn't. Argh. I highly doubt that it  didn't work because of your instructions. A lot of USBs have stop working for me--usually when I don't shut down cleanly. 
*Thank you for being so thorough~* I appreciate people who don't half-*** things. :'D

The next issue is that when the USB boots (I checked the .iso, it seemed  fine)... It.. Well... It doesn't boot. It's worked fine before, but my  ubuntu USBs usually crash on me like this. /Sigh.
**It just gives me this "no operating system found" or "not bootable" carp-in-a-pond.**
**I assure you people that this USB worked fine with ubuntu before.**
I really, really cannot identify the problem. Disk utility insists it's  bootable in the partition flags (relevant? I haven't the slightest), of  universal disk format... etcetc. 
But for some reason it's mounted in /cdrom in root. Whaaaat. My other  live USBs did not even go there. Nautilus doesn't mount it  automatically, which I could probably get around if I needed to...  Anyway, I can't unmount/safelyshutdown no matter what since it gives me  this "busy" message. Or this:
"Device is mounted and no online capability in fsck tool for file system"
Wat. I no compretend.

Can anybody provide me with further assistance? Perhaps something on it is broken, and I need to manually repair it or something. Before I go  hysterical (shut it ye judgementals--I'm not being melo, I have every  right to go mad--I've been at this way too long--I have a Pringles CAN  on my shoulder right now... Okay, maybe that last line was melo. More lame than melo, but...).

---

### Post by Thewhistlingwind on 2011-05-31
> **Baniita said:**
>  I appreciate people who don't half-*** things. :'D

Good, cause I'm never helping you again.

That was completely unnecessary..........

---

### Post by Baniita on 2011-05-31
@wind: ...Er.. XD" Sorry. Seriously.
[edit--...OWAIT. What? What was unnecessary? At first I thought you meant the way I dealt with the files--hurr. That line totally wasn't referring to you, by the way. Chah there practically wrote a walkthrough, so I just meant it in general. I'm surrounded by apathetic tards most of the time, is why.]

> The point was to get usable files after ubuntu boots it so that you can restart AGAIN then boot it.
You could also try the conv and output flags.
I just... Have no clue what that means. I restarted several times... No matter what, I couldn't boot it. I wasn't sure what you meant and just assumed that I shouldn't bother you any more, since you already sounded agitated. . v." Yes yes, call me an idiot all you like. Conv/output flags... The only thing I can associate that with are partition flags. And I'm pretty sure that's not it.

Actually, it is silly how long it took me to figure out just how to put the files on the USB without it giving me permission/'unique file' shet. /Shakes head.

---

