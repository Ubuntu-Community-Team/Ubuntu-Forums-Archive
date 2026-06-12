---
title: "dd question on bash"
date: 2010-05-26
forum: General Help
---

### Post by pizza-is-good on 2010-05-26
I have a question. I am currently overwriting a flash drive with zeros using dd.

To be specific, I used```
sudo dd if=/dev/zero of=/dev/sdb bs=1G count=100
```I started the process about an hour ago. The drive is 32GB. I know that it is still working and writing, because my cpu usage is high, my ram is at about 50% when it is usually at 10%, and the flash drive is hot! I expect it to go on for a few more hours, especially since the dive write average speed is 2 MB/s.

I am just wondering, if I were to restart the process, is there a way that I could have the terminal show me the progress? Right the last line that it shows me is the prompt for my password. I looked through ```
man dd
``` but did not find it useful in finding an argument that would show progress.

Thanks,

~pizza

---

### Post by Serpher on 2010-05-26
Just use this when in the flash drive's directory:

```
df -h
```

---

### Post by baddog144 on 2010-05-26
dd doesn't actually provide any sort of progress bar by default. However there are various means of adding one, such as the ones described here: [http://www.commandlinefu.com/commands/view/1868/watch-the-progress-of-dd]("http://www.commandlinefu.com/commands/view/1868/watch-the-progress-of-dd")

HTH

---

### Post by KeyserSoze93 on 2010-05-26
> **baddog144 said:**
> dd doesn't actually provide any sort of progress bar by default. However there are various means of adding one, such as the ones described here: [http://www.commandlinefu.com/commands/view/1868/watch-the-progress-of-dd]("http://www.commandlinefu.com/commands/view/1868/watch-the-progress-of-dd")

HTH

My personal favourite is pv. Install pv from the package manager, and then run:

```

dd if=/dev/sdX | pv | dd of=/dev/sdY

```

---

### Post by pizza-is-good on 2010-05-26
Hey fellas,

thanks for the replies.

I imagine that if I were to use pv, then I would edit my original command from

```
sudo dd if=/dev/zero of=/dev/sdb bs=1G count=100
```to

```
sudo dd if=/dev/zero | pv | dd of=/dev/sdb bs=1G count=100
```is that correct?

A question about pv. What info will it display?

now, as for df -h, can I use that while dd is running?

The problem with that is that /dev/sdb is not mounted right now, so I can't go into the directory.

Again, thanks for the replies. It's probably been about 2 hours now and I'm still waiting, but if I ever have to do this again, I'm definitely trying your suggestions, as I would like to know how much it has gotten done. Right now, I'm just planning on leaving the computer on until it is done. Oh well....

---

### Post by Serpher on 2010-05-26
Just use another terminal window, or if you're not using GNOME terminal, Ctrl + Alt + F1-6 are all individual terminals. Also if sdb isn't mounted, you're not creating that image file to the correct place. I think you're actually executing that command wrong now that I look at it.

```
sudo -i
mkdir /media/mnt/
mount /dev/sdb /media/mnt/
dd if=/dev/zero of=/media/mnt/anyfilenamehere bs=1G count=100
```

When you go into another terminal simply do this:

```
cd /media/mnt/
df -h
```


'df -h' will display the size of the image file, and the file just gets bigger and bigger as it reaches the full size of your USB.

---

