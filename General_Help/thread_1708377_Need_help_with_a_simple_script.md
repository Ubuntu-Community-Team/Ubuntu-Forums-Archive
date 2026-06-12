---
title: "Need help with a simple script"
date: 2011-03-16
forum: General Help
---

### Post by sr_guy on 2011-03-16
I pulled this command from winff. I want to create a simple script so I can encode video files via CLI that will ask these series of questions and then encode the file. I'm terrible at coding, so that's why I'm here =)  Here is the command:

```

ffmpeg -i -f avi -r 29.97 -vcodec libxvid -vtag XVID -s 720x480 -aspect 16:9 -maxrate -b -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2

```


1. Enter the directory and filename to be encoded
2. Enter the Desired bitrate. (ie 3000k)
3. Enter the desired Max bitrate. (ie 5000k)
4. *echo output of dir name and file* Is this the correct filename/directory? Y or N.

Then hit enter. If no, aborts encoding, if yes, it goes on to encode.

Those of you wondering,  I like to log into CLI via ssh while at work and encode that way opposed to remote desktop.

---

### Post by seawolf167 on 2011-03-16
Sounds like you want to use some variables inside a script.

Something like

```
#!/bin/bash[FONT=monospace]
[/FONT]clear
read -p "Please enter your variable1 : " variable1
read -p "Please enter your variable2 : " variable2
read -p "Please enter your variable3 : " variable3
...your big long command here...
echo "Encoding $variable1 at $variable2 for $variable3..."

```You can pass the date/time/etc as a variable as well

```
$(date +%m-%d-%y)
```

---

