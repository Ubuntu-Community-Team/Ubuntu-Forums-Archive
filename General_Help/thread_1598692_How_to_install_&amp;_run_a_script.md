---
title: "How to install &amp; run a script?"
date: 2010-10-16
forum: General Help
---

### Post by lxnski on 2010-10-16
Dear forums,

I found a very simple script online which I would like to install. So far I have pasted the script into geedit and saved it. The next question for me is now that I have done that, how do I actually install it? I know I would have to do something such as 

sudo install ______ /usr/local/bin 

but when I attempt to do that I get the message 

"install: cannot create regular file `usr/local/bin': No such file or directory"

Say that I have the script saved on my desktop, how would I go about installing it?

Im very sorry, this must be a total n00b question but I am very new to ubuntu and still exploring it.
:confused:

---

### Post by mr clark25 on 2010-10-16
what scripting language is it in? (if you don't know, past the first line of it here)

just curious, what does it do?

---

### Post by lxnski on 2010-10-16
I found it online to download videos from youtube and then convert them into mp3 files. These are basically the directions for installing listed on the site:

```
gedit youtube2mp3

...and paste the following script:

x=~/.youtube-dl-$RANDOM-$RANDOM.flv
youtube-dl --output=$x --format=18 "$1"
ffmpeg -i $x -acodec libmp3lame -ac 2 -ab 128k -vn -y "$2"
rm $x

Save and close gedit. Now install the script somewhere easily accessible.

sudo install youtube2mp3 /usr/local/bin

Now you can convert youtube videos into mp3 files by using the following command (including the double quotes):

youtube2mp3 "youtube-link" "mp3-file.mp3"



```

---

### Post by mr clark25 on 2010-10-16
that script looks like a bash script, but it is a little above me. i know some bash scripting, but not enough to (fully) understand that script.


looks someone else will need to help you...

---

### Post by btindie on 2010-10-16
You don't need to 'install' it, just copy it to a directory that's in your path. You could place it in /usr/local/bin or in your own bin directory. Run the following commands from the terminal
```
[ -d ~/bin ] || mkdir ~/bin
```That creates a bin directory in your home directory if it doesn't already exist. Then type
```
echo $PATH
```you should see something that looks like "/home/${USERNAME}/bin:........". If it doesn't then you'll have to logout and back in for it to update itself, that can be done after you've finished the below.
```
cp ~/Desktop/<script_name> ~/bin/
```That copies your script to your bin directory
```
chmod +x ~/bin/<script_name>
```That makes your script executable, something that will be missing if you saved it as a regular text file and is required to run it directly from the terminal.

You can now run your script from the terminal as you would any other.

That's a SHELL script, DASH under Ubuntu, and should have the following as the very first line to have it run with the correct program
```
#!/bin/sh
```

---

### Post by drewsus on 2010-10-16
Might I suggest [www.video2mp3.net](www.video2mp3.net)

---

