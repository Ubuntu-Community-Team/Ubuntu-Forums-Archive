---
title: "Clipboard sharing in Xephyr?"
date: 2010-03-15
forum: General Help
---

### Post by nerdopolis on 2010-03-15
Hi. I am trying to make a Live CD which makes use of Xephyr. Xephyr seems to do the job I need, however it seems that I can't copy things from the rest of my windows to paste into the Xephyr window, and copy things out of the Xephyr window to paste into the rest of the windows.

I have the live CD here [http://ubuntuforums.org/showthread.php?t=1417911](http://ubuntuforums.org/showthread.php?t=1417911) , and if people using the live cd can not copy things into the Xephyr window, then I imagine it will be very frustrating to use.

is there any way to share the clipboard between two Xservers? Any thing I am missing?

---

### Post by nerdopolis on 2010-03-16
I managed to find a clipboard manipulation program named xsel it allows you to grab or set the clipboard of a specified x display. 

With that, I managed to write a little script to sync between two X displays, for as long as the script is running. It takes it 1 second or so for it to update the data when the clipboard changes, and if you were to lose one of the X severs, and bring it back, it resets the clipboard for both.

I have it below: it requries xsel to be installed. you can install xsel with ```
sudo apt-get install xsel
```Once thats installed, copy the script below into a file, and make it executable. if you where to share between :0 and :1 run it in the terminal like so

```
/path/to/file :0 :1 
```

```
#! /bin/bash
firstxserver=$1
secondxserver=$2
#set the variables to the default
echo . | xsel --display $firstxserver -b -i 
echo . | xsel --display $secondxserver -b -i
clipboard=.

while [ 1 ]
do
#get the values of the clipboard
firstdislpayclipboard=$(xsel --display $firstxserver -b -o)
seconddislpayclipboard=$(xsel --display $secondxserver -b -o)

#if the first x servers clipboad chages
if [ "$firstdislpayclipboard" != "$clipboard" ]
then

#if it doesnt change to be blank
if [ $(echo $firstdislpayclipboard | grep ^$ -c) -ne 1 ]
then
#set the appropriate variables to be the contents of the first comand
seconddislpayclipboard=$firstdislpayclipboard
clipboard=$firstdislpayclipboard
xsel --display $firstxserver -b -o | xsel --display $secondxserver -b -i
else
#if it is blank set it to be .in case if its because the x server went down
echo . | xsel --display $firstxserver -b -i 
fi

fi

#if the second x servers clipboad chages
if [ "$seconddislpayclipboard" != "$clipboard" ]
then

#if it doesnt change to be blank
if [ $(echo $seconddislpayclipboard | grep ^$ -c) -ne 1 ]
then
#set the appropriate variables to be the contents of the first comand
firstdislpayclipboard=$seconddislpayclipboard
clipboard=$seconddislpayclipboard
xsel --display $secondxserver -b -o | xsel --display $firstxserver -b -i
else
#if it is blank set it to be .in case if its because the x server went down
echo . | xsel --display $secondxserver -b -i 
fi

fi

sleep 1
done



```Now when you copy text in the :0 you can paste it in :1, and if you where to copy text in :1 you can paste it in :0 

I hope this  helps somebody along the lines

---

