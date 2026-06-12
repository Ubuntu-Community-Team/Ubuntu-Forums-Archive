---
title: "Disk activity every 2 seconds."
date: 2011-01-25
forum: General Help
---

### Post by Edho on 2011-01-25
Hello.

Installed Maverick 10.10 on my new desktop.
Asus Mobo , Amd Athlon proc.
3 G mem, Graka on board.

Seems it is all ok.

One thing i do not like.
Even when no program is running...
Led from hard drive lights every 2 seconds or so.

I think it is no good for the lifetime of the hard drive.

Suggestions please?


Thank You in advance.

---

### Post by mikewhatever on 2011-01-25
Look at the output of **ps aux** when no program is running. Many processes can be accessing the disk without you launching programs. Is it really like you say, every two seconds all the time? There are ways to reduce disk activity, but are you sure you want to?

---

### Post by Edho on 2011-01-25
Can't judge the output from  -ps aux-.

Is it common? ( the activity )

Seems unnecessary to me.


Hope i get a solution here.

---

### Post by mikewhatever on 2011-01-25
The following command will temporarily increase the writeback timeout from the default of 5 seconds to 15:
```
sudo sysctl -w vm.dirty_writeback_centisecs=1500
```

If you see the difference, make it permanent by running the following once:
```
echo vm.dirty_writeback_centisecs=1500 | sudo tee -a /etc/sysctl.conf
```

---

### Post by Edho on 2011-02-04
Thanks for trying to help.


Surprise now...
:confused:When  i put a disc in the cd/dvd drive... the HD activity is gone.

---

### Post by JKyleOKC on 2011-02-04
> **Edho said:**
> When  i put a disc in the cd/dvd drive... the HD activity is gone.That indicates that the activity you were seeing was the dvd driver polling the drive to detect whether you had inserted a disc. It wasn't the HD at all -- the LED flashes for any internal drive access. You could just keep a CD in the drive; one of my older boxes requires one before it will detect the drive at boot time!

---

### Post by Edho on 2011-02-06
> **JKyleOKC said:**
> That indicates that the activity you were seeing was the dvd driver polling the drive to detect whether you had inserted a disc. It wasn't the HD at all -- the LED flashes for any internal drive access. You could just keep a CD in the drive; one of my older boxes requires one before it will detect the drive at boot time!

Yes, it's a easy sollution.


Tx all.

---

