---
title: "Linux-unfriendly university lectures"
date: 2010-04-12
forum: General Help
---

### Post by MrNatewood on 2010-04-12
My university has online lectures for some courses.
Unfortunately, it is made with Microsoft technologies and thus does not work for me in ubuntu.

2 years ago someone posted this script to make it work on linux:
```
#! /usr/bin/ruby

if /mms:\/\/.*\.wmv/=~ARGV[0]
    temp_string=ARGV[0].dup
    temp_string["mms://"]="rtsp://"
    `vlc --rtsp-tcp #{temp_string}`
else
    puts "Usage: vid_lectures mms://filename.wmv"
end 
```

Trouble is, I don't have a clue in how to make this script do anything.
I don't know much about programming and such...
Tried to drag-and-drop it to greasemonkey, turns out it only accepts javascript files.

Any ideas on how to progress on this?

---

### Post by 98cwitr on 2010-04-12
Its a bash script:

save it as a .sh file (i guess to your home dir would be fine)...run it with sudo permissions in terminal...should work.

---

### Post by prodigy_ on 2010-04-12
> **98cwitr said:**
> Its a bash script:
No. It's a Ruby script. The extension should be **.rb** and to run it, you'll need Ruby installed: ```
sudo apt-get install ruby
```
It's possible that you'll also need to install something else. I'm not really familiar with Ruby, sorry.

---

### Post by -humanaut- on 2010-04-12
Yep. That is indeed a ruby script. I have to say though it seems like you should be able to view whatever files without it though. just a thought looks like there just .wmv files. a simple sudo apt-get install ubuntu-restricted-extras should allow you to view them.?

---

### Post by 98cwitr on 2010-04-12
woops...should have known that by the "ruby" on the first line :? :P

---

### Post by MrNatewood on 2010-04-13
Thanks, actually running it as .sh works. :)

Tough, it is a bit awkward to have to copy paste each link to the terminal.

Any chance anyone would know how to convert it to something greasemonkey can work with?

As far as I can tell what it does is change the "mms://" to "rtsp://" and run it with vlc.

---

### Post by prodigy_ on 2010-04-13
Try VLC plugin: ```
sudo apt-get install mozilla-plugin-vlc
```
VLC uses its own codecs, so most probably you won't need anything else.

---

