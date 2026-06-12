---
title: "Help with installing: Songbird, Thunderbird and Aptana Studio"
date: 2010-03-19
forum: General Help
---

### Post by sshea on 2010-03-19
First off I'd like to apologize if this is the wrong section of the forum, if it is in the wrong place would a moderator be so kind as to move it to the right place. Secondly I'm very new to Linux so my knowledge is quite limited. Now onto the problems at hand, I'll give you the versions of each program I suppose and then it might be easier to help me.

_Songbird:_ Version = 1.4.3     |     BuildID = 1438
_Thunderbird:_ Version = 3.0.3     |     BuildID  = 20100227141902
_Aptana Studio 2:_ Version = 2.0.4.1268158907     |     BuildID = 1268158907

Right so the problem's I'm having:

_Songbird:_ (Fixed)
I downloaded it off the songbird website, extracted it when it finished but could not find details on how to install it. Now it does work, all i have to do is go to the containing folder and run the file labeled "songbird" it does not have a .txt or anything after its name. When I click run or run in terminal it starts up and works fine BUT it is not in the "Applications" tab.

_Thunderbird:_ (Fixed)
This is exactly the same as the problem I'm having with Songbird so perhaps the fix is similar?

[U]Aptana Studio
[/U]I downloaded this program as I was interested in polishing up my web designing skills after a quick 1 year course on it last year in school. This was the first Macromedia Dreamweaver 8 like program that I found so I thought why not. Dreamweaver 8 is what I was using in school. If you can recommend another program that'd be great but otherwise help installing would be nice. Now as I said I downloaded it. Extracted the files and looked for the README which as with another program told me how to install said program. I cant find it and none of the other files in the folder mention how to install it.

So those are my problems. If you need any more information do ask.

Thank you in advance :)

---

### Post by mridkash on 2010-03-19
You first download Songbird from website. The file will be a .tar.gz file I think. Right click on the file and select "Extract Here" and then it will open a dialog. A folder will now be created with the name "Songbird" go into that folder and double click on "songbird" file it will ask you "run" "display" etc, select "run".

I don't know exactly about thunderbird, but try this method with thunderbird also. But you don't need to download thunderbird from website. Open Applications > ubuntu software center and type thunderbird in search and install it ,simple.

---

### Post by sshea on 2010-03-19
I do that yet it does not install. It runs fine but it doesn't actually install

---

### Post by mridkash on 2010-03-19
oops, I didn't read your post properly. 
So you already got Songbird working and want to install it in applications menu. Thats simple, right click on applications menu and select "Edit Menus" and then go to "Sound & Video" and click on "new item". There add the path to songbird file that you ran manually before.

Edit: You can also go to System > preferences > Main Menu to edit the menus

---

### Post by Chesamo on 2010-03-19
> **sshea said:**
> _Songbird:_
I downloaded it off the songbird website, extracted it when it finished but could not find details on how to install it. Now it does work, all i have to do is go to the containing folder and run the file labeled "songbird" it does not have a .txt or anything after its name. When I click run or run in terminal it starts up and works fine BUT it is not in the "Applications" tab.
Here's what I did:

1. Create a folder in your Home directory called "songbird" (capitalization is IMPORTANT... *NIX is case-sensitive)
2. Extract the contents of the tarball into there
3. System > Preferences > Main Menu
4. Navigate to the "Sound and Video" section
5. "New Item"
6. In "Command" put: ~/songbird/songbird
7. In "Name" put: Songbird
8. Click on the springpad, click "Browse" and navigate to the songbird directory
9. Click Open and select the Songbird icon. Click OK.

> **sshea said:**
> [U]Thunderbird:
[/U]This is exactly the same as the problem I'm having with Songbird so perhaps the fix is similar?
run this in Terminal:
```
sudo apt-get install thunderbird
```

> **sshea said:**
> [U]Aptana Studio
[/U]I downloaded this program as I was interested in polishing up my web designing skills after a quick 1 year course on it last year in school. This was the first Macromedia Dreamweaver 8 like program that I found so I thought why not. Dreamweaver 8 is what I was using in school. If you can recommend another program that'd be great but otherwise help installing would be nice. Now as I said I downloaded it. Extracted the files and looked for the README which as with another program told me how to install said program. I cant find it and none of the other files in the folder mention how to install it.
I'm unfamiliar with this program, but I assume the method would be similar to the Songbird installation.

---

### Post by LifesGod on 2010-03-22
Hi there, trying to install songbird, I followed all the steps posted, the icon folder appeared to be empty and I ended up with the springboard on the launcher panel and "unable to launch application"
Can anyone help me? This is my first foray into this forum so I hope I can find any answer I might receive :-) many thanks!

---

### Post by rahilm on 2010-03-22
1)songbird
You can either install from the ppa : [https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)
Or. if you have root privelages, extract the contents of the .tar file to a folder songbird in /opt. then make a link in "/usr/bin" to the executable. Then it is easy to put in the menu. You have to just enter "songbird" instead of the path. You can also launch songbird just by typing "songbird" in the terminal.
2)Thunderbird
Same as songbird except that there is no good repository. The thunderbird in the repository is actually a very old version.

---

### Post by LifesGod on 2010-03-22
would code: sudo apt-get install songbird  work for songbird too?

---

### Post by rahilm on 2010-03-22
> **LifesGod said:**
> would code: sudo apt-get install songbird  work for songbird too?
no. that command works only if songbird is in the repositories, which it isn't. but once you install the ppa above, you can do sudo apt-get install songbird

---

### Post by LifesGod on 2010-03-22
thanks, but it feels a bit complicated. i usually have a friend who helps me but he's o/s for 6 months, and am usually ok with following instructions but feeling a bit lost with this one .. oh well, thanks anyway :)

---

### Post by rahilm on 2010-03-22
just run:
```

sudo add-apt-repository ppa:songbird-daily/ppa && sudo apt-get update && sudo apt-get install songbird

```
it will do some downloading and you are done with installing songbird.

---

