---
title: "Kino problems"
date: 2006-03-23
forum: General Help
---

### Post by deadgobby on 2006-03-23
OK here is the scoop snoops,
  I have sucessesfully install a Leadtek Winfast TV 2000 XP card. Ubie
saw it and was able to hook up my DVD, VCR, and Cable to it. I can now
watch more smut on my puter. HEHEHE! Any hoo, now I want to able to
capture/record vids. This is not working. Kino sees the vidcard, how
ever I am getting IEEE1394 errors in Kino. Here is what it says.
"IEEE1394 Subsytem is not respound, raw1394 mod must be loaded and
must have read and write access to dev/raw1394"  The DV Export is 
DV1394 device: /dev/ieee1394/dv/host0/PAL/out
 I am haven the same problems with other apps like DVR and other vid editors. I tried running the live CD of MeadianLinux and same thing. I would about to give my first born to solve this problem. HEHEH. Any help would be greatful.
](*,) 
 
Gobby

---

### Post by anders_gud on 2006-03-23
[QUOTE=deadgobby]Here is what it says.
"IEEE1394 Subsytem is not respound, raw1394 mod must be loaded and
must have read and write access to dev/raw1394" [/QUOTE]
Try:
sudo chown root:video /dev/raw1394

permissions should look like this:
rw-rw----   1 root video

---

### Post by deadgobby on 2006-03-23
chown: cannot access `/dev/raw1394': No such file or directory

I check in synaptic and no dir in their. Any input would be great.
:-D

---

### Post by queenorych on 2006-03-23
I am not sure what a winfast tv card is, but I'm guessing a btxxx card.  I don't think Kino will capture from these cards.  Kino.dv.org lists

Capture
    * IEEE 1394 (Linux 1394) capture and export
    * IEEE 1394 transport control (AV/C)
    * USB Jog/Shuttle transport control

So I think kino will only capture from a firewire source.

You need a v4l or bttv capture program.  I am not sure what works best these days.  Last I used xawtv.  I think vlc will work.  Mencoder, ffmpeg as well.  THough check packeges.ubuntu.com search for v4l or bttv in the description.  I'd capture to Huffman encoding, then import it into kino.  Also check out avidemux.  Not sure if its in the repos.

---

### Post by deadgobby on 2006-03-23
None of mechen is helping. Grrr. Is there some thing I need to tweek to get this to work?

---

### Post by jdusablon on 2006-05-18
> Try:
sudo chown root:video /dev/raw1394

permissions should look like this:
rw-rw---- 1 root video
Hey! that worked beautifully on Dapper! Thanks!
Makes you wonder why this security setting isn't part of the install.

Also, video capture is better done with another program. Kino is focused on DV importing, like home movies.

---

### Post by greenstar on 2006-05-24
Worked for me on Dapper also. That's all I had to do, and Kino detected my Sony DCR-TRV130. Next I need to test my Canopus ADVC-50 to see if it works.


Greenstar

---

### Post by fsman on 2006-05-25
I raised a bug report on having to change raw1394 to video group. I got a reply stating that this is a very very bad security risk.

[https://launchpad.net/distros/ubuntu/+source/kino/+bug/6290](https://launchpad.net/distros/ubuntu/+source/kino/+bug/6290)

looks like kino needs to be changed to use /dev/dv1394-0 not /dev/raw1394

best advice is to using the dv1394 driver and live without the av/c control

---

### Post by markitos on 2006-06-15
[QUOTE=anders_gud]Try:
sudo chown root:video /dev/raw1394

permissions should look like this:
rw-rw----   1 root video[/QUOTE]

Thanks, this one helped me also, Dapper and kde

M

---

