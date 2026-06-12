---
title: "HELP! Synchronizing folders and CP -r Command?"
date: 2012-07-24
forum: General Help
---

### Post by HoCo xXSamXx on 2012-07-24
Ok, So I have been trying to sync my BlackBerry with my ubuntu computer. So far I have this:
```
cp -r '/home/sam/.gvfs/media on sam_playbook/music' '/home/sam/Music'

cp -r '/home/sam/.gvfs/media on sam_playbook/videos' '/home/sam/Videos'

cr -r '/home/sam/.gvfs/media on sam_playbook/photos' '/home/sam/Pictures'
```

It does do the job, but when I run it I just get a blank terminal screen. So my questions:

1. IS there anyway to have terminal show the progress while executing the commands?

2. Is using the CP command the correct way to do this?

---

### Post by Habitual on 2012-07-24
Sam:
```

rsync -avz "/home/sam/.gvfs/media on sam_playbook/music" /home/sam/Music
rsync -avz "/home/sam/.gvfs/media on sam_playbook/videos" /home/sam/Videos
rsync -avz "/home/sam/.gvfs/media on sam_playbook/photos" /home/sam/Pictures

```should work.

---

### Post by HoCo xXSamXx on 2012-07-24
Thank! Worked Perfectly!

---

### Post by bryncoles on 2012-07-24
or you could add 'v' for 'verbose'

```
cp -vr '/home/sam/.gvfs/media on sam_playbook/music' '/home/sam/Music'

cp -vr '/home/sam/.gvfs/media on sam_playbook/videos' '/home/sam/Videos'

cr -vr '/home/sam/.gvfs/media on sam_playbook/photos' '/home/sam/Pictures'
```

Should work.  Type ```
man cp
``` into the terminal for more information

---

### Post by HoCo xXSamXx on 2012-07-24
I think rsync would be better becuase is would *sync* instead of just *copy* the data

---

### Post by Habitual on 2012-07-24
Glad it worked out.

---

