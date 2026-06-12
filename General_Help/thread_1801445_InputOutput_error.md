---
title: "Input/Output error"
date: 2011-07-10
forum: General Help
---

### Post by ThanosIsKing on 2011-07-10
I've been using my 2TB external hard drive with Ubuntu with no problems for a while now, but recently there is one folder on the drive that I cannot access. Whenever I try to open the folder I get "error stating file: Input/output error". I scoured the forums and noticed that the folder might just be dirty because I failed to use the Windows option to "safely unplug" the drive (bolstered by the fact that neither avast! or Malwarebites found anything). My question is how do I "clean" the folder so I can use it again?

---

### Post by Habitual on 2011-07-10
mount it in WinTendo and do a "safe" remove and then plug it back into your current OS?

---

### Post by ThanosIsKing on 2011-07-10
> **Habitual said:**
> mount it in WinTendo and do a "safe" remove and then plug it back into your current OS?

Tried that (plug external into Windows comp, select safe remove, plug into Ubuntu). Didn't work. Still can't access my folder.

EDIT: In folder view, the folder just isn't there. I know it's present because I can see it in Windows, but it's nowhere to be found in folder view in Ubuntu.

---

### Post by Habitual on 2011-07-10
partition type of the 2TB external hard drive?

IOW: I formatted this drive as ...

---

### Post by ThanosIsKing on 2011-07-10
> **Habitual said:**
> partition type of the 2TB external hard drive?

IOW: I formatted this drive as ...

NTFS. Partition type is HPFS/NTFS (0x07)

---

### Post by psusi on 2011-07-10
Check the output of dmesg for kernel errors.  If it is a disk media error, then you may need to replace the disk because it is failing.  If it is fs corruption, you may need to run chkdsk on it from windows.  You might also check the SMART status in the disk utility.

---

### Post by ThanosIsKing on 2011-07-10
> **psusi said:**
> Check the output of dmesg for kernel errors.  If it is a disk media error, then you may need to replace the disk because it is failing.  If it is fs corruption, you may need to run chkdsk on it from windows.  You might also check the SMART status in the disk utility.

SMART status checks out. All processes are performing in top shape. Though when I did a dmesg check I get several messages with:

"Buffer I/O error on device sdb1, logical block 1953571496" (blocks are through 1953571504)
"sd 11:0:0:0: [sdb] Unhandled error code"
"sd 11:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK"
"sd 11:0:0:0: [sdb] Read(10): 28 00 74 71 23 67 00 00 80 00"
"end_request: I/O error, dev sdb, sector 1953571687"

I can't find any lines that specifically tell me whether it's a disk media error or a fs corruption. I'm thinking something's up with Ubuntu though, since the folder is missing only on Ubuntu. I find it fine on Windows.

---

### Post by psusi on 2011-07-10
That's weird... that looks like the drive was disconnected.

What happens if you try this:

```

dd if=/dev/sdb bs=512 skip=1953571687 of=/dev/null count=1
```

---

### Post by ThanosIsKing on 2011-07-11
> **psusi said:**
> That's weird... that looks like the drive was disconnected.

What happens if you try this:

```

dd if=/dev/sdb bs=512 skip=1953571687 of=/dev/null count=1
```

Even weirder is that I get a message saying "dd: opening 'dev/sdb': No such file or directory"

---

### Post by psusi on 2011-07-11
Then yea, it looks like the drive went offline/unplugged.

---

### Post by ThanosIsKing on 2011-07-11
> **psusi said:**
> Then yea, it looks like the drive went offline/unplugged.

Then how do I get my folder to show up in Ubuntu?

It's very weird that this one folder is the only one that's no longer "there" in Ubuntu.

---

### Post by psusi on 2011-07-11
Get the disk to light back up ( unplug and plug it back in? ) and then try the dd command again.

---

### Post by ThanosIsKing on 2011-07-11
> **psusi said:**
> Get the disk to light back up ( unplug and plug it back in? ) and then try the dd command again.

Same thing happens.

---

### Post by psusi on 2011-07-11
What do you mean the same thing happens?  You still don't have a /dev/sdb when you plug the drive back in?

---

### Post by ThanosIsKing on 2011-07-11
> **psusi said:**
> What do you mean the same thing happens?  You still don't have a /dev/sdb when you plug the drive back in?

Exactly.

---

### Post by psusi on 2011-07-11
Does the drive show up as another letter?  If it isn't showing up at all, then it's toast.

---

### Post by ThanosIsKing on 2011-07-12
> **psusi said:**
> Does the drive show up as another letter?  If it isn't showing up at all, then it's toast.

I apologize for this, still quite new to Ubuntu and all, but "another letter"? Like when it's in Windows? Because I've never had my drives appear as letters in Ubuntu.

Still don't know why it would be toast. It's just one folder, albeit an important one (with all my scripts). Works fine in Windows.:???:

---

### Post by psusi on 2011-07-12
Another letter as in sdc instead of sdb.

---

### Post by ThanosIsKing on 2011-07-12
> **psusi said:**
> Another letter as in sdc instead of sdb.

Ah. Nope, disk utility shows the drive showing up as /dev/sdb

---

### Post by psusi on 2011-07-12
Please post the EXACT output of the dd command.

---

### Post by ThanosIsKing on 2011-07-12
"dd: opening 'dev/sdb': No such file or directory"

That's actually what I'm putting in when Konsole starts up. Should I be inputting this command while Konsole is in the directory for the external? If so, how do I do that?

---

### Post by psusi on 2011-07-12
You made a typeo: you are missing the leading /.

---

### Post by ThanosIsKing on 2011-07-12
> **psusi said:**
> You made a typeo: you are missing the leading /.

Derp.#-oBut now I'm getting "permission denied".

---

### Post by psusi on 2011-07-12
sudo

---

### Post by ThanosIsKing on 2011-07-12
> **psusi said:**
> sudo

Another derp. Forgot sudo goes before pretty much anything. :P

So that makes the folder show up, but I still get the input/output error when trying to access it.

---

### Post by psusi on 2011-07-12
Now what does the last 10 lines or so of dmesg show?  And can you then run dd without the skip argument?

---

### Post by ThanosIsKing on 2011-07-13
> **psusi said:**
> Now what does the last 10 lines or so of dmesg show?  And can you then run dd without the skip argument?

Last 10 lines of dmesg are:

ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present
wlan0: deauthenticating from 00:0f:b3:79:76:35 by local choice (reason=3)
wlan0: deauthenticating from 00:0f:b3:79:76:35 by local choice (reason=3)
wlan0: direct probe to AP 00:0f:b3:79:76:35 (try 1)
wlan0: direct probe responded
wlan0: authenticate with AP 00:0f:b3:79:76:35 (try 1)
wlan0: authenticated
wlan0: associate with AP 00:0f:b3:79:76:35 (try 1)
wlan0: RX AssocResp from 00:0f:b3:79:76:35 (capab=0x471 status=0 aid=2)
wlan0: associated

I also ran the dd without the skip. Still can't access the folder. What happens is:

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0236471 s, 21.7 kB/s

---

### Post by psusi on 2011-07-13
Hrm... doesn't seem to be any error there.  With the skip argument in what does dd say?

---

### Post by ThanosIsKing on 2011-07-13
With the skip argument the same thing happens:

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0236649 s, 21.6 kB/s

---

### Post by psusi on 2011-07-13
That's odd... last time reading that sector got an error.  Try dropping both the skip and count arguments... let it read the whole bloody disk and see if it screws up anywhere.

---

### Post by ThanosIsKing on 2011-07-13
> **psusi said:**
> That's odd... last time reading that sector got an error.  Try dropping both the skip and count arguments... let it read the whole bloody disk and see if it screws up anywhere.

Well, nothing SEEMS to be happening. I don't get any sort of message whatsoever. I've left it running since you posted this suggestion in case it was taking its sweet time (probably 300+ GB taken up on the thing already). That was over 7 hours ago. I get no message at all. Could the bs command be too small in size (512 B seems tiny when there's so much stuff to sift through)?

---

### Post by psusi on 2011-07-13
Nothing means it's still working... give it a little longer.

---

### Post by ThanosIsKing on 2011-07-14
> **psusi said:**
> Nothing means it's still working... give it a little longer.

Finally finished checking. This is what I got:

3907029168+0 records in
3907029168+0 records out
2000398934016 bytes (2.0 TB) copied, 63089 s, 31.7 MB/s

And my files are back. Don't know why a simple dd would do that. Thanks!

---

