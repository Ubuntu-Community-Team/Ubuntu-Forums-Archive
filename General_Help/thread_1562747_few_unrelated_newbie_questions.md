---
title: "few unrelated newbie questions"
date: 2010-08-28
forum: General Help
---

### Post by dedede on 2010-08-28
I finally got ubuntu and I really like it, but there are some things that really bug me, I'm not sure if they are a bug or something I dont know well enough (probably latter).

1) When I put the headphones on, the audio continues to come also from the speakers. That is pretty annoying, is this a driver problem? I wouldnt want to 'go here, do that' each time I restart my PC or plug in the headphones, so is there a way to simply tell it to mute speakers each time I put on headphones?

2) I cant set default applications for filetypes! Each time I do that Ubuntu completely ignores what I set. I do "open with other applications" and " remember this application for "this" files, but next time its the default application again.

3) I cant edit files/folders except a few. I know Windows Vista/7 is like this too, but you simply have to click extra button after a warning/or input your admin password and youre good to go. In Ubuntu I'm not given any window to put my password in, just an error. I can go to Terminal and type "sudo nautilus", but come on, do that every single time?

---

### Post by ankspo71 on 2010-08-28
Hi,
3) Ubuntu (and most other distributions) has it set up this way so system files stay protected... Not just from the user, but from hackers, potential viruses, malware, etc. If you frequently have to edit files and folders outside of your home directory it is easy to create a menu entry or panel application launcher using _gksudo nautilus_ as the command. That way you can simply click on it then enter the password. It's best not to use the command 'sudo' with graphical applications though because that might eventually cause permissions problems. Sudo is for doing work inside the terminal and gksudo is for doing things outside the terminal basically.

If this question was about a separate hard drive that you have  dedicated to file storage, you can use the chown command to take ownership of that hard drive's partition, which is what I do.
sudo chown -R yourname:yourname /path/to/other/partition
Hope this helps.

---

### Post by DeMus on 2010-08-28
> **dedede said:**
> I finally got ubuntu and I really like it, but there are some things that really bug me, I'm not sure if they are a bug or something I dont know well enough (probably latter).

1) When I put the headphones on, the audio continues to come also from the speakers. That is pretty annoying, is this a driver problem? I wouldnt want to 'go here, do that' each time I restart my PC or plug in the headphones, so is there a way to simply tell it to mute speakers each time I put on headphones?

2) I cant set default applications for filetypes! Each time I do that Ubuntu completely ignores what I set. I do "open with other applications" and " remember this application for "this" files, but next time its the default application again.

3) I cant edit files/folders except a few. I know Windows Vista/7 is like this too, but you simply have to click extra button after a warning/or input your admin password and youre good to go. In Ubuntu I'm not given any window to put my password in, just an error. I can go to Terminal and type "sudo nautilus", but come on, do that every single time?

2)
In Nautilus (file manager) right-click a file and choose Properties. In that window choose TAB "Open with".
Select the program or when it is not in the list add it (you most likely find it in /usr/bin)
Then the next time you click on this file-type it will open with the program you selected.

---

### Post by polardude1983 on 2010-08-28
For me on 1) of yours I actually LOVE that Ubuntu does this. I hate how i have to unplug my headphones in windows to listen through my speakers, since i ALWAYS have my headphones plugged in :)

---

### Post by dedede on 2010-08-28
> **ankspo71 said:**
> Hi,
3) Ubuntu (and most other distributions) has it set up this way so system files stay protected... Not just from the user, but from hackers, potential viruses, malware, etc
Again, I understand that, but still, whats the difference if you will be prompted to allow that operation and asked to write the admin password? Windows didnt have anything like that for protecting files, but they added it in Vista, the way I described above. I see no reason why this method would be more volnurable to hackers than doing it in command line.

> 2)
In Nautilus (file manager) right-click a file and choose Properties. In that window choose TAB "Open with".
Select the program or when it is not in the list add it (you most likely find it in /usr/bin)
Then the next time you click on this file-type it will open with the program you selected.OK, works. Anyways, I would love to help Ubuntu improve how I can, so is this a known issue? Should I report it?

> For me on 1) of yours I actually LOVE that Ubuntu does this. I hate how i  have to unplug my headphones in windows to listen through my speakers,  since i ALWAYS have my headphones plugged in :smile:
Well not me. Pretty much any audio device I have seen works like that, so I dont see why it should be the default behavior.

---

### Post by ankspo71 on 2010-08-28
> **dedede said:**
> Again, I understand that, but still, whats the difference if you will be prompted to allow that operation and asked to write the admin password? Windows didnt have anything like that for protecting files, but they added it in Vista, the way I described above. I see no reason why this method would be more volnurable to hackers than doing it in command line.


I must have misunderstood the question a little. Actually, I don't know why Linux distributions would rather ask the user for a password instead of presenting the user with a simple "allow" or "don't allow" dialog. It would make things easier. It was annoying for me at first too, but I got used to it in a couple of weeks (plus having a shorter password helped me out too).

---

### Post by dedede on 2010-08-28
Hehe, I think you misunderstood that again.
I didnt mean why Linux asks for password, I ment why doesnt it? (it doesnt right?)
I mean it asks, but in the terminal only. Whats the difference?
Can't it just ask for the password in the file browser? Rather than making me go to terminal and type the 'sudo' thing?

I'm familiar with command lines/terminals, but for other people this will be a headache. And I still think I'm wasting my precious time each time I do it.

---

### Post by hawthornso23 on 2010-08-28
Most people don't find themselves needing to edit protected files routinely. The sudo thing is a small price to pay for a secure system.

---

### Post by dedede on 2010-08-28
'Most people', hmm. I dont know who you mean, some of my applications store their data in such a place. Saying its a 'small price to pay' is like saying 'whats the problem with triple-clicking?'. Oh and sorry, but what 'price' do you mean here? If I was asked to enter my password in the file browser instead of starting a terminal and entering there, what would be the difference? You can say 'its not a big deal', but i know that for ME it is quite annoying.

---

### Post by 3rdalbum on 2010-08-28
Why don't you install the "nautilus-gksu" package from Software Center. Then when you next log in, you can right-click on any file or folder and choose "Open As Administrator". Saves a trip to the terminal.

The feature you suggest where your privileges can be automatically elevated after a prompt the way Vista does it, has been proposed and is feasible on Linux, but there's not much interest in actually implementing it. I'd probably be opposed to it - I think there *should* be that little barrier in the way of system file modification, that causes the user to think. A simple "Allow this action?" dialog box is too easy to just click "OK" to, without the user actually thinking about whether what they are doing might affect the system or other users.

In other words, if you want to edit system files, you should have to think "I need root for this" rather than just "Get this dialog off my screen".

---

### Post by dedede on 2010-08-28
> **3rdalbum said:**
> Why don't you install the "nautilus-gksu" package from Software Center. Then when you next log in, you can right-click on any file or folder and choose "Open As Administrator". Saves a trip to the terminal.
Something like this by default would be great. Especially for people migrating from Windows OSs (90% ?). packages are great, but for people with no or very limited internet this can be harder than it seems.
Anyway, after logging off and in, it started to work.

> The feature you suggest where your privileges can be automatically elevated after a prompt the way Vista does it, has been proposed and is feasible on Linux, but there's not much interest in actually implementing it.
This isnt the area of programming I have experience with, but is it really such a difficult, complex thing to implement?

> I'd probably be opposed to it - I think there *should* be that little barrier in the way of system file modification, that causes the user to think. A simple "Allow this action?" dialog box is too easy to just click "OK" to, without the user actually thinking about whether what they are doing might affect the system or other users.
I see where youre coming from. But if its 'people who have no idea what they are doing and do it even after a warning' VS 'people who get annoyed by having to start a terminal to edit some of their program files every single time', I would choose the latter.

---

### Post by dedede on 2010-08-28
The audio driver issue question is still unanswered

---

### Post by Regunirun on 2010-08-28
I'm no Linux sound expert, but I can share that on my iMac running Linux and my System76 (linux out of the box) laptop running Lucid and Maverick respectively, it's either internal or headphones. I think that this is the default functionality. I would assume that the driver probably has control over this, and that there's likely a way to override that setting.

---

### Post by dedede on 2010-09-05
Bump

---

### Post by dedede on 2010-09-07
I use audio programs alot, so this is a big deal.

---

### Post by dedede on 2010-09-12
Bump

---

### Post by Elfy on 2010-09-12
You might be better starting a thread to deal specifically with the sound issue.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I would also make sure to give the make and model of the laptop.

You might find a search using your make and model as well results in some help - [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

