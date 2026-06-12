---
title: "Rhythmbox &amp; Konversation"
date: 2010-05-07
forum: General Help
---

### Post by Nahlidge on 2010-05-07
If this is in the wrong section, I apologize. The way the forum is setup is confusing, to me.




Alright, I really like Rhythmbox, it's my audio-player of choice on any linux distro I use.
I also like Konversation, though I really can't stand using the KDE gui, I prefer Gnome. 

Being that I like both of the above mentioned apps, I had a problem getting Rhythmbox to
display song information in IRC channels in Konversation, and when I googled it I couldn't
find anything or anyone who has (been trying since 8.04). Finally, I figured a way to do it.

This was all done on a fresh install of Ubuntu 10.04 x64.
Using Rhythmbox 0.12.8 and Konversation 1.2.3



After setting things up, I installed Konversation
```
**sudo apt-get install -y konversation**
```I also installed Conky (I use it for hardware monitoring and a few other things)
```
**sudo apt-get install -y conky**
```Alright, I got conky setup the way I want it and began my endless search via google for
a way to get Rhythmbox working within Konversation. After about 40 minutes of finding
nothing I decided to play in Konversation with its few scripts that come with it. 
I was having lots of fun with */cmd <various commands>*, like i'd use in terminal.

Thats when I remembered the conkyRhythmbox python script I'd often use to play song
information inside conky on my desktop for when I had Rhythmbox minimized.

So I installed it (using **kaivalagi**'s _Basic Install: Method 1_ ([COLOR=Blue][click here]("http://ubuntuforums.org/showthread.php?p=5843297")[/COLOR]))

Once installed, I copied the sample conkyRhythmbox.template sample to my home
directory, renamed it, along with changing the format.

Copy it to your home directory
```
**sudo cp /usr/share/conkyRhythmbox/example/conkyRhythmbox.template /home/<user>/.K-Rb.temp** 
<enter your password>
```The default conkyRhythmbox.template file contains the following:
```
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
```I changed it to:
```
**[--datatype=ST]: "[--datatype=TI]" by [--datatype=AR] ([--datatype=PT]/[--datatype=LE])**
```Outcome in Konversation:
[00:00:00] <Nick> Playing/Paused: "Title of Track" by Artist(s) (0:00/0:00)


In Konversation, go to _Settings_ then _Configured Konversation..._
Under the _Behavior_ tab, click on _Command Aliases_
On the left, click on New to create a new command.


At the bottom, in the textbox for* Alias* I put:
```
**rb**
```And for *Replacement*, I put:
```
**/exec cmd conkyRhythmbox --template=/home/<user>/.K-Rb.temp**
```Click _Apply_ to save the command and _OK_ to close out the setting window.


In konversation, on any channel/query, type:
```
**/rb**
```**I attached a screenshot of it at the bottom of the post. **
I hope you enjoy it as much a I do (I know most people will just overlook this
or think it's just useless, but I like to share my music into the channels, and 
now I can use both my favorite irc client and music player.)

I added my .K-Rb.temp (renamed to K-Rb.txt) as an attachment, so you should
be able to copy it directly and rename it to .K-Rb.temp and use the Bold text symbol
things I have (look at the Screenshot.png to see what I mean)

:)

---

