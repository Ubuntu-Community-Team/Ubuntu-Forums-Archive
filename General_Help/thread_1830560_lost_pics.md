---
title: "lost pics"
date: 2011-08-21
forum: General Help
---

### Post by cowboy7305 on 2011-08-21
i want to know if there is any programs that will do really deep scans of my hard drive that had been reformatted to find lost pics ,and can also scan for files on flash drives same reason lost pics

---

### Post by Script Warlock on 2011-08-21
you might try testdisk or photorec

---

### Post by seventyeights on 2011-08-21
Install testdisk which includes photorec.

```
sudo apt-get install testdisk
```

make a recovery directory and enter it

```
mkdir recovered-files
cd recovered-files
```

run photorec as root
```
sudo photorec
```

choose your drive (I recommend the flash first, you'll quickly get an idea how it works) and then choose your filetypes. For the main drive, surely deselect txt,html, and gif or else you'll be pulling up tons of all kinds of websurfing junk. If it ever had windows, then deselect exe and cab also.

Hope you get your stuff back.

---

### Post by coffee412 on 2011-08-21
Hi.

Ive done file recovery with testdisk and it does a great job. Takes a long time but the results are good. As long as you have not over-written the sectors its going to work. However you end up with a bunch of numbered directories. I ended up with like 500 directories with files in them. 

You might find this helpful. I wrote a script to run that copies the certain files (jpg, png, mpg ect) from the directories to just one. Just adjust it to your needs pathwise.

> #!/bin/bash
        updatedb
for i in $( locate /home/coffee/Downloads/tony/*.jpg ); do
           cp "$i" /home/coffee/Downloads/tony-jpg 
        doneGood luck.

---

### Post by cowboy7305 on 2011-08-22
Thanks have run it and i have found every pic i have taken before and after the ones i wanted  next trick is go back and take them again

---

### Post by sleepingdragon on 2011-08-22
"foremost" saved me from a failed backup. Had to scrape my backup drive to get my photos back. Worked a charm, and you can select what you're looking for. Be warned though, if you have .mpg/.avi, it may recover them as indivudual frames (minus the sound). Nothing worse than 30,000+ frames of me doing something stupid whilst drunk. 

Also supports dd images if you've already done a drive image.

---

