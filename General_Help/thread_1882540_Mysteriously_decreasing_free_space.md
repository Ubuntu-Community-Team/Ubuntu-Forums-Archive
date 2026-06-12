---
title: "Mysteriously decreasing free space"
date: 2011-11-17
forum: General Help
---

### Post by Nick42 on 2011-11-17
Hello,

I started to have a very strange problem in last days. My free space is constantly decreasing even though I'm not doing anything that would result in that. I get those free space back once I type "touch /forcefsck" and reboot the machine.

In around half an hour, I lose around 10 GBs.

Here's the current situation:

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              91G   50G   37G  58% /
none                  3.9G  736K  3.9G   1% /dev
none                  3.9G  1.3M  3.9G   1% /dev/shm
none                  3.9G  100K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock

Available space on /dev/sda5 was around 46 GB after reboot with a fsck check.

Here's another useful information:

$ du -hs * | sort -hr
18G     Dir1
12G	Dir2
1.2G	Dir3
227M	Dir4
198M	Dir5
2.1M	Dir6
12K	Dir7
8.0K	Dir8
4.0K	Dir9
4.0K	Dir10

Note: I've replaced actual directory names with DirX. 

As you see, the total does not make up 50 GB total at all.

Any comments?

PS: Oops, the available space is already 35 GB now.

Thanks in advance!

---

### Post by Nick42 on 2011-11-17
Ok, problem found and solved. It was about Spotify client.

Here you can find information:
[http://getsatisfaction.com/spotify/topics/spotify_is_writing_an_obscene_amount_of_information_to_error_file](http://getsatisfaction.com/spotify/topics/spotify_is_writing_an_obscene_amount_of_information_to_error_file)

Basically (Do it at your own risk!):

1. Recreate Music folder under your home folder 
2. Change content of .config/user-dirs.dirs -> "XDG_MUSIC_DIR="$HOME/Music"
3. Erase .xsession-errors.log and .xsession-errors.old files

---

