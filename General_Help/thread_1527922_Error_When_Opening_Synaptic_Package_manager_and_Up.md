---
title: "Error When Opening Synaptic Package manager and Update Manager"
date: 2010-07-09
forum: General Help
---

### Post by Garetty on 2010-07-09
Every time I try to open one of these I get this error: 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by tekkidd on 2010-07-09
Go to the terminal and type in  

```
sudo dpkg --configure -a
```

---

### Post by Garetty on 2010-07-10
Alright. I got this:
```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 43784 package 'rsyslog':
 `Depends' field, reference to `zlib1g': version contains ` '

```

---

### Post by WorMzy on 2010-07-10
Unless someone else can suggest a better solution, you may need to manually edit that file. Can you press Alt+F2 and run 'gedit /var/lib/dpkg/status'. Press Ctrl+I and type in the popup-box '43784', then select the entire section that line is in, and copy and paste it here so we can look at it.

---

### Post by Garetty on 2010-07-10
> **WorMzy said:**
> Unless someone else can suggest a better solution, you may need to manually edit that file. Can you press Alt+F2 and run 'gedit /var/lib/dpkg/status'. Press Ctrl+I and type in the popup-box '43784', then select the entire section that line is in, and copy and paste it here so we can look at it.
gedit could not detect the character encoding...

---

### Post by WorMzy on 2010-07-10
Oh dear, that really doesn't sound good. It looks as though your status file has become corrupted.

I've found a couple of posts about that on other forums, and it seems that moving (renaming) the file and using a backup can fix the problem. So try
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak
```
followed by
```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then try running
```
sudo dpkg --configure -a
```
again.

---

### Post by Garetty on 2010-07-10
Alright. This time I got this:
```
dpkg: parse error, in file '/var/lib/dpkg/updates/0099' near line 0:
 newline in field name `#padding'

```

I ran that like you said last time and I got this:
```
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#pad
```

---

### Post by WorMzy on 2010-07-10
What the..?

Your system seems to having some serious hiccups. If I were you, I'd consider booting into a LiveCD and fscking (fsck = [COLOR="Red"]f[/COLOR]ile[COLOR="Red"]s[/COLOR]ystem [COLOR="Red"]c[/COLOR]hec[COLOR="Red"]k[/COLOR]) your Ubuntu partition, something seems to have gone seriously wrong somewhere.

After booting into a LiveCD, run 'sudo blkid' and identify which is your Ubuntu partition (e.g. [COLOR="Red"]sda3[/COLOR])

Then run fsck with a command similar to this:
```
sudo e2fsck /dev/[COLOR="Red"]sda3[/COLOR]
```

If memory serves, it should automatically detect and fix any problems it encounters.

Afterwards (or if you'd rather skip the fscking), you can try removing that file. On my Lucid installation, the update directory is empty, so I doubt that that file is integral to the workings of dpkg. If you want to keep a backup of it, just in case then run the following:
```
cp /var/lib/dpkg/updates/0099 ~/0099
```
to remove the original file, run:
```
sudo rm /var/lib/dpkg/updates/0099
```

Try 'sudo dpkg --configure -a' again.

---

### Post by Garetty on 2010-07-10
Well I'm not sure what worked... but it all is working now. Thanks for your help. ;)

---

### Post by WorMzy on 2010-07-10
No problem, happy to help. :)

---

