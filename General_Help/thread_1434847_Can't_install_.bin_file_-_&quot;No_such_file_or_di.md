---
title: "Can't install .bin file - &quot;No such file or directory&quot;"
date: 2010-03-20
forum: General Help
---

### Post by S3loth on 2010-03-20
I am trying to install Adobe AIR. I downloaded the [.bin file]("http://get.adobe.com/air/") from their home page onto my Desktop. In terminal, I went to my Desktop and made the file executable via ```
chmod +x AdobeAIRInstaller.bin
```. Now I am using the command ```
./AdobeAIRInstaller.bin
``` to run it, but the error "No such file or directory" comes up. I've installed .bin files before with no problems, so I don't understand what would be wrong with this one.

---

### Post by dcstar on 2010-03-20
> **S3loth said:**
> I am trying to install Adobe AIR. I downloaded the [.bin file]("http://get.adobe.com/air/") from their home page onto my Desktop. In terminal, I went to my Desktop and made the file executable via ```
chmod +x AdobeAIRInstaller.bin
```. Now I am using the command ```
./AdobeAIRInstaller.bin
``` to run it, but the error "No such file or directory" comes up. I've installed .bin files before with no problems, so I don't understand what would be wrong with this one.

And $5 says you have a 64-bit system and are trying to install some 32-bit binary you found somewhere........

---

### Post by S3loth on 2010-03-20
That seems to be the problem...strange though that I have had AIR working on past Ubuntu versions on this computer. Guess its just another program I'll have to not use until the 64 bit version, which is starting to become a long list :lolflag:

---

### Post by dcstar on 2010-03-21
> **S3loth said:**
> That seems to be the problem...strange though that I have had AIR working on past Ubuntu versions on this computer. Guess its just another program I'll have to not use until the 64 bit version, which is starting to become a long list :lolflag:

What list?, even Adobe have a native 64-bit version of the Flash plugin now.

---

### Post by S3loth on 2010-03-21
Well, I am exaggerating a bit but it just seems like the 32-bit to 64-bit switch is causing a lot of problems, whether a 32-bit program won't run on a 64-bit system, or vice-versa. While the 64-bit flash did solve a lot of problems for me, it won't work on Hulu either. Anyway, just me think out loud.

---

### Post by 3rdalbum on 2010-03-21
I've installed Adobe Air on 64-bit. It sucked, but I didn't get a "no such file" error.

Two possible things:

1. Use 'sudo' - an installer needs to put files in root-owned locations.

```
sudo -i
chmod a+x AdobeAIRinstaller.bin
./AdobeAIRinstaller.bin
```

2. Try dragging the installer to the terminal so it automatically fills in the file path.

---

### Post by S3loth on 2010-03-21
> **3rdalbum said:**
> I've installed Adobe Air on 64-bit. It sucked, but I didn't get a "no such file" error.

Two possible things:

1. Use 'sudo' - an installer needs to put files in root-owned locations.

```
sudo -i
chmod a+x AdobeAIRinstaller.bin
./AdobeAIRinstaller.bin
```

2. Try dragging the installer to the terminal so it automatically fills in the file path.

That made it work! Or rather I should say it installed. We have yet to see if it will still run smoothly haha Thanks!

---

### Post by 3rdalbum on 2010-03-21
I'm glad it worked for you. Unfortunately I can't help you in your search for an Air program that actually does anything useful.

---

### Post by S3loth on 2010-03-21
> **3rdalbum said:**
> I'm glad it worked for you. Unfortunately I can't help you in your search for an Air program that actually does anything useful.

TweetDeck! The only reason I have any interest in AIR. Very useful not just for Twitter, but also getting feeds from other social websites.

---

