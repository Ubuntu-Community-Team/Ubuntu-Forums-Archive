---
title: "extract multiple 7z files in multiple folders"
date: 2011-06-14
forum: General Help
---

### Post by DeMus on 2011-06-14
HI,
I have a large amount of 7z files in multiple folders which I need to extract.

The directory structure is like this:

/main-folder/
   multiple subfolders/
      1 or more 7z files per subfolder

I would like to get the output of this action in one separate folder, all together in 1 folder.

How can I do this? I have tried several 'programs' I found using Google but non work for me.

---

### Post by DeMus on 2011-06-14
I know it is very early to bump the thread, sorry for this, but I would be very thankful if somebody could help me. So guys, please, help me do this.
Thank you.

---

### Post by DeMus on 2011-06-15
Thank you all so very much for helping me out here. The Ubuntu forum is just fantastic. For 3 years I help whenever I can and when I need help there is nobody who want to/can help me. Great.

---

### Post by nothingspecial on 2011-06-15
> **DeMus said:**
> Thank you all so very much for helping me out here. The Ubuntu forum is just fantastic. For 3 years I help whenever I can and when I need help there is nobody who want to/can help me. Great.

Nice attitude :roll:

You wouldn't have been able to help with this one either since you had to ask.

I've never extracted a 7zip folder in my life but maybe something like

```
7z -e main-folder/*/*.7z -o output_directory
```

Don't know if that will do what you require because I don't have any 7z files to test it on.

---

### Post by ruffEdgz on 2011-06-15
I don't know which program you are using for archiving to a 7zip but I downloaded the p7zip application on the repo:
```
aptitude install p7zip
```
I can see why there is some problem since the app isn't very robust as lets say 'tar'. I made a small script that you will have to place into the destination folder:
```

#!/bin/bash
IFS=$'\n'
zfiles=$(find $1 -name "*.7z" -type f)

if [ $(echo $* | wc -w) -ge 2 ]; then
        echo "Please only use one path"
        exit
fi
for i in $zfiles; do
        echo "Decompressing package: $i"
        /usr/bin/p7zip -d $i
done

```
Once this is in a file and executable, you should be able to run the following command:
```
sudo ./script <main folder path>
```
Before running, the main command I run to gather all the file names can be found below so please run this command before running the script to make sure its grabbing the information you need it to grab:
```
find <main folder path> -name "*.7z" -type f
```

PS - if you aren't using p7zip, please tell me as I can change the application and test it out to make sure it works.

Cheers!

---

### Post by Slim Odds on 2011-06-15
> **DeMus said:**
> Thank you all so very much for helping me out here. The Ubuntu forum is just fantastic. For 3 years I help whenever I can and when I need help there is nobody who want to/can help me. Great.

So now you've joined the ranks of the ungrateful. People who like to complain because they don't get what THEY consider to be timely support for FREE from an all VOLUNTEER group of USERS that come here in our SPARE TIME.

Pitiful

---

### Post by DeMus on 2011-06-15
> **ruffEdgz said:**
> I don't know which program you are using for archiving to a 7zip but I downloaded the p7zip application on the repo:
```
aptitude install p7zip
```
I can see why there is some problem since the app isn't very robust as lets say 'tar'. I made a small script that you will have to place into the destination folder:
```

#!/bin/bash
IFS=$'\n'
zfiles=$(find $1 -name "*.7z" -type f)

if [ $(echo $* | wc -w) -ge 2 ]; then
        echo "Please only use one path"
        exit
fi
for i in $zfiles; do
        echo "Decompressing package: $i"
        /usr/bin/p7zip -d $i
done

```
Once this is in a file and executable, you should be able to run the following command:
```
sudo ./script <main folder path>
```
Before running, the main command I run to gather all the file names can be found below so please run this command before running the script to make sure its grabbing the information you need it to grab:
```
find <main folder path> -name "*.7z" -type f
```

PS - if you aren't using p7zip, please tell me as I can change the application and test it out to make sure it works.

Cheers!



First of all I want to apologize for my behavior. I know I was very impolite. I do know everyone here is doing this in their spare time, for the fun, for learning from others, etc. I do the same.
Now I needed help and couldn't find a working program on the net so I tried it here. After a whole day I had no response what so ever, so i got p*ssed. Sorry.
It's just that I needed the help asap and couldn't wait any longer.
Happily I got help now and also help which worked.

@ruffEdgz
Thank you for your program. It did the trick after a small change. I replaced: 
```
zfiles=$(find $1 -name "*.7z" -type f)
with
zfiles=$(find <main folder path> -name "*.7z" -type f)
where <main folder path> is the path I use.
```

Thank you so much, also to the others who replied. Once again I am sorry for my behavior. I try not to do it again.

---

### Post by ruffEdgz on 2011-06-15
> **DeMus said:**
> First of all I want to apologize for my behavior. I know I was very impolite. I do know everyone here is doing this in their spare time, for the fun, for learning from others, etc. I do the same.
Now I needed help and couldn't find a working program on the net so I tried it here. After a whole day I had no response what so ever, so i got p*ssed. Sorry.
It's just that I needed the help asap and couldn't wait any longer.
Happily I got help now and also help which worked.

@ruffEdgz
Thank you for your program. It did the trick after a small change. I replaced: 
```
zfiles=$(find $1 -name "*.7z" -type f)
with
zfiles=$(find <main folder path> -name "*.7z" -type f)
where <main folder path> is the path I use.
```

Thank you so much, also to the others who replied. Once again I am sorry for my behavior. I try not to do it again.

No worries. If I would have seen this earlier, I would have helped then ;)

Glad it worked with your change as well since I didn't know the path to your main folder, I wanted to give you a way to do with by placing it next to the script.

Cheers!

---

