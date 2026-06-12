---
title: "Share your clipboard with Xephyrs clipboard"
date: 2010-03-17
forum: General Help
---

### Post by nerdopolis on 2010-03-17
For anyone that used Xephyr you probably realized that the clipboard on your main display and the clipboard in Xephyr are seperate.

I wrote a little script to sync between two X  displays, for as long as the script is running in the background. It takes it 1 second or  so for it to update the data when the clipboard changes, and if you were  to lose one of the X severs, and bring it back, it resets the clipboard  for both.

I have it below: it requires xsel to be installed. you can install xsel  with ```
sudo apt-get install xsel
```Once thats installed, copy  the script below into a file, and make it executable. if you where to  share between :0 and :1 run it in the terminal like so:
 ```
/path/to/file :0 :1
```

This is the script:
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
#if it is blank set it to be .in case if its because the x server went  down
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
#if it is blank set it to be .in case if its because the x server went  down
echo . | xsel --display $secondxserver -b -i 
fi

fi

sleep 1
done

 
```

Now when you copy text in the :0 you can paste it in :1, and if  you where to copy text in :1 you can paste it in :0 

I hope this  helps somebody along the lines

---

