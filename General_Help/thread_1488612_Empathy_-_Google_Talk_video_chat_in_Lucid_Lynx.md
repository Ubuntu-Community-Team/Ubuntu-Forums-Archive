---
title: "Empathy - Google Talk video chat in Lucid Lynx"
date: 2010-05-20
forum: General Help
---

### Post by GOTO_sHELL on 2010-05-20
Good day everyone!

    I would be glad to use Google Talk video chat in Empathy? Did anyone make it work? Share please some manual.

---

### Post by temporos on 2010-05-20
*shameless bump*

Yes, I'm having trouble starting video and audio chats via Empathy's Google Talk, as well.  Any help on this would be appreciated.

**Edit: **The "Audio Call" and "Video Call" items in the Empathy Contact menu are greyed-out.  I can't select them during a text chat.

---

### Post by temporos on 2010-05-27
**Update: **I've managed to figure out why the video chat/audio chat features were disabled in Empathy's Google Talk, but now I can't figure out how to get the video chat to work.  When I attempt to start a video/audio chat, it brings up a chat window, but then disconnects.  When another user attempts to start a video or audio chat with me, I hear Empathy "ringing," but I can't figure out how to answer it (no prompt or dialogue window appears)!

Does anyone know how to fix this?  I can't find another thread dealing with this specific issue.  If I missed it, please let me know.

OS: Ubuntu 10.04 Lucid Lynx Netbook Edition
Hardware: ASUS EeePC 1005HA

---

### Post by fragos on 2010-05-27
Voice and video chat aren't supported by Gmail on Linux. It's not an Empathy issue.

---

### Post by temporos on 2010-05-27
> **fragos said:**
> Voice and video chat aren't supported by Gmail on Linux. It's not an Empathy issue.
Actually, it *is* an Empathy issue.  Empathy is a multi-server client.  That is, it makes Yahoo! think you're using Yahoo! Messenger, Google think you're using Google Talk, etc..

Think of Empathy as a sort of "data scrubber."  You give it information, and it "cleans" it for use in the chat connection of your choice.  Similarly, it receives data from that connection and cleans it so your operating system knows what to do with it.

So, to the problem at-hand, according to Google's servers, you don't have a Linux issue.  You have a connection issue.  Since Empathy is the software that "sanitizes" such data streams, it *must* be an Empathy issue.

---

### Post by fragos on 2010-05-27
Here is Gmail's own words, "Unfortunately we do not yet have voice and video chat for Gmail available for your operating system." But of course that may only refer to browser based. Empathy 2.30.1 does show who has a camera on-line with a camera icon. I attempted to initiate a video call to another Gmail user that Empathy recognized as having a camera and being on-line. I could see my my image but only the avatar of the person I was calling. The status said "connecting..." This particular person always leaves their PC on running Windows 7 so his not responding to the connection may just mean he's not physically there. Is this what you're getting? I hung up on my side and now his camera icon is gone. Perhaps he unplugged it because he didn't want to talk now.

---

### Post by temporos on 2010-05-28
> **fragos said:**
> "Unfortunately we do not yet have voice and video chat for Gmail available for your operating system."
That's for only the browser-based chat feature in Gmail.

> **fragos said:**
> I could see my my image but only the avatar of the person I was calling. The status said "connecting..."
When I attempted to initiate a video call, the video call window came up, but then immediately disconnected.  When someone attempted to initiate a video call with me, I heard the ringing sound-effect, but there was no button or window to answer it.

---

### Post by aggiemarine07 on 2010-05-28
it works for me but what i found out is that the other person has to have audio/video chat enabled on their gmail account.

i found this out when i tried to see if it was an empathy or google problem. I had empathy set up with my gmail account (under ubuntu 10.04) and then i had my Google Apps account open in a browser (under a virtual session of winxp using Google Chrome as the browser). 

Initially when i say my Google Apps account come online in Empathy, it did like normal and had the audio call/video call grayed out. However, after installing the audio/video chat plugin that Google uses for windows for gtalk, those two options were NOT grayed out.

So it seems that it is indeed enabled and working but it will be grayed out unless the other person has audio/video setup on their machine as well.

EDIT: also you can know if they have this capability setup because there will a microphone (for only audio) or a webcam (audio and video) icon next to their username, near their profile picture.

---

### Post by fragos on 2010-05-28
> **aggiemarine07 said:**
> it works for me but what i found out is that the other person has to have audio/video chat enabled on their gmail account.


Which means if you're a Linux user you're out of luck since Gmail won't let Linux systems enable audio/video chat. In this case Gmail is the server for Jabber. One of these days it'll work for us to.

---

### Post by rcktsingh on 2010-05-30
I have been facing this problem since so long. Whenever I have to audio/voice call with my friends, I have to reboot my machine and go to Windows to use GTalk there. Sometimes gets frustrating !!](*,)

Isn't there any workaround for this ?

---

### Post by timcredible on 2010-05-30
i think you should try to get your friends to use something else

---

### Post by mzavada on 2010-06-01
I comes across the same issue when trying to start an audio chat with my mom who is running ubuntu just like me.  we both have Gmail accounts and i see the microphone icon lit up.  When i click on the microphone icon another window pops up with the word connecting at the bottom.  
            The first time we tried it she heard the ringing however she was not able to connect.  Any time we tried after that she did not hear any ringing and it would always say connecting and nothing else.  Weird.

---

### Post by aggiemarine07 on 2010-06-01
There has been a similar issue with [empathy and using SIP]("https://bugs.launchpad.net/ubuntu/+source/telepathy-sofiasip/+bug/526158"). Empathy seems to not be integrated very well with Voice or Video. The link is pointed toward this bug with SIP. 

I have also built the latest (as of this past Sunday, 30 MAY 2010) Empathy 2.31.2 from source and the issue is still there. From reading other forums, the problem seems to lie with empathy's, either total lack or inadequate support for common audio codecs (i.e. G722, PCMA, etc.) that are used by services like SIP and Gtalk. 

So hopefully they will fix this problem with future releases but as of the latest build (2.31.2 on 30 MAY 2010), it has not been fixed.

---

### Post by temporos on 2010-06-02
I agree, the problem lies with the client itself and not with Google's servers.  However, if a codec issue is really the problem, then why is there no notification window, button, or any other way to answer an incoming audio/video call?  That's more likely a bug, not an incompatibility.

---

### Post by John Bennett on 2010-06-05
Oddly, when using Empathy with a Gtalk user, I can hear them, but they can't hear me.

No video of course.

---

### Post by cynical99 on 2010-06-09
On my side, with a standard installation of ubuntu 10.04, using a gmail account, I managed to get a video call with another person with a standard installation of ubuntu 10.04, using a gmail account. The only problem : his webcam freezes quite often. The video I get freezes, also his own image freezes, whereas mine continues working at both sides.

I first thought to an hardware problem on his side, but with skype it works really well.

Hope it might help... and someone can find out why his camera freezes with empathy and not with skype.

Cheers

---

### Post by pablotdl on 2010-06-10
Well, I have Karmic and audio calls work great. The problem I have is with video.

My computer hasn't got a camera, but I cannot receive the video from my other laptops. It's shown on the calling computer (running Karmic too), but not on mine.

Any idea what can it be? Skype seems to work fine.

---

### Post by mrspacklecrisp on 2010-06-11
@Temporos: You are quite silly. When someone calls you, their name blinks on the list. Double-click his or her name and then click "accept"

I'm having problems too. If I call them, I can connect. I get their video and sound. They just don't get my video nor my sound. When they call me, the application can't connect at all. I had to be very careful about installing the correct plugins, which really shouldn't have been necessary considering it's the chat client that comes with the os. Point is, I have the right codec but it's still failing me.

---

### Post by temporos on 2010-06-11
> **mrspacklecrisp said:**
> @Temporos: You are quite silly. When someone calls you, their name blinks on the list. Double-click his or her name and then click "accept".

... and you're quite Texan.  I knew Texas was a "whole other country," but I was still under the impression that you used manners there.  >_>  Maybe if you didn't wear your cowboy hats or sombreros so tight...

Yes, when I double-click on the blinking name, no dialog window appears, and no buttons appear next to their name or anywhere else on the chat window.  It just rings and rings until they hang up.

---

### Post by mrspacklecrisp on 2010-06-11
> **temporos said:**
> ... and you're quite Texan.  I knew Texas was a "whole other country," but I was still under the impression that you used manners there.  >_>  Maybe if you didn't wear your cowboy hats or sombreros so tight...

Yes, when I double-click on the blinking name, no dialog window appears, and no buttons appear next to their name or anywhere else on the chat window.  It just rings and rings until they hang up.

Jesus Christ. And I thought Canadians were nice. I wasn't trying to be condescending, I just didn't read any post in which you said that you'd actually done that. It seemed to me that you had assumed a dialogue would pop up without you doing anything, which would not have been an unreasonable assumption (I personally did that the first time and was very confused) So no problems here, I was simply trying to be helpful.

And now we've established that we have the same problem. I had an epiphany last night about this: Since I know I have the correct codec, yet it still doesn't work, so could this possibly be a security thing? Some setting somewhere that is trying to protect the user by interrupting the connection?

---

### Post by amp3030 on 2010-06-13
Empathy can make audio/video calls with google talk, as long as it has codecs it needs. Try this:
```

sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight

```
taken from [here]("https://help.ubuntu.com/community/Empathy").

---

### Post by benedict779 on 2010-06-15
Guys , i'm using ubuntu 10.04 netbook remix ,
i can make video calls to my friend who's using gmail in windows 7 . i can see his video and v r able to talk each other. but he never get my video.

i thinks the problem is with my empathy, its not sending any video

---

### Post by dysonsphere23 on 2010-06-17
> **amp3030 said:**
> Empathy can make audio/video calls with google talk, as long as it has codecs it needs. Try this:
```

sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight

```
taken from [here]("https://help.ubuntu.com/community/Empathy").

I did that and still the connection drops out, is choppy, and will not stay connected. Empathy then freezes, windows darken, and unresponsive.

---

### Post by green69 on 2010-06-18
> **amp3030 said:**
> Empathy can make audio/video calls with google talk, as long as it has codecs it needs. Try this:
```

sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight

```
taken from [here]("https://help.ubuntu.com/community/Empathy").

I have all these packs installed but I can't enable audio o video chat, neither through gtalk account. The audio call/video call options is gray. Please can anybody help me?

---

### Post by sdirector on 2010-06-19
> **benedict779 said:**
> Guys , i'm using ubuntu 10.04 netbook remix ,
i can make video calls to my friend who's using gmail in windows 7 . i can see his video and v r able to talk each other. but he never get my video.

i thinks the problem is with my empathy, its not sending any video

This describes my exact problem as well. Using empathy on Ubuntu Lucid on one computer and gmail web browser on Windows 7 on the other end. On the ubuntu side, I can see the preview of my video image and I can see the remote video image that the Windows computer is sending. On the windows computer, I see the video preview of the local image and a greyed out icon instead of the remote video.

The exact same symptoms appaear if I use pidgin... so I'm pretty confused.

---

### Post by impresionist on 2010-06-29
Well, I use empathy only for chat text, and with Lucid I was interesting in use it also as SIP client, but I guess that empathy work only for texting, no voice services neither in jabber, neither in SIP... I installed as you referred to 
sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight

and also, according to empathy, all this packedges:
gnome-common
gettext
libglib2.0-dev
gtk-doc-tools
libxml2-dev
libtelepathy-glib-dev
libmissioncontrol-client-dev
libtelepathy-farsight-dev
libx11-dev
libgtk2.0-dev
libcanberra-gtk-dev
libgstreamer-plugins-base0.10-dev
libebook1.2-dev
libnotify-dev
libunique-dev
libgnome-keyring-dev
libenchant
libpanelapplet

Vut it's absolutly no change... only chating... 

it will be really a Boombbb if empathy could serve voice, chat, video, and as a skype client... jejeje
It's much to ask for ):P

---

### Post by green69 on 2010-07-01
> **impresionist said:**
> Well, I use empathy only for chat text, and with Lucid I was interesting in use it also as SIP client, but I guess that empathy work only for texting, no voice services neither in jabber, neither in SIP... I installed as you referred to 
sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight

and also, according to empathy, all this packedges:
gnome-common
gettext
libglib2.0-dev
gtk-doc-tools
libxml2-dev
libtelepathy-glib-dev
libmissioncontrol-client-dev
libtelepathy-farsight-dev
libx11-dev
libgtk2.0-dev
libcanberra-gtk-dev
libgstreamer-plugins-base0.10-dev
libebook1.2-dev
libnotify-dev
libunique-dev
libgnome-keyring-dev
libenchant
libpanelapplet

Vut it's absolutly no change... only chating... 

it will be really a Boombbb if empathy could serve voice, chat, video, and as a skype client... jejeje
It's much to ask for ):P

Hi, I finally obtained make empathy work even for voice and video chat (and SIP of course). A part from the rep. you already mencioned I've just installed gnome-audio rep through synaptic.

I hope this works for you too. :D

---

### Post by YannBuntu on 2010-07-02
To do video+audio calls with a Windows Gtalk user, you need 3 things :
- Empathy with Telepathy PPA ([https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa))
- ubuntu-restricted-extra
- a Jabber account (a gmail adress is ok)

---

### Post by rcktsingh on 2010-07-04
!! - (i meant to delete my post.)

---

### Post by errebepe on 2010-07-13
I've got it working:

- Following YannBuntu's suggestion, installed Empathy from PPA:

```
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update
sudo apt-get dist-upgrade # I suppose "apt-get install empathy" works as well

```

- Then, following [Empathy's FAQ]("http://live.gnome.org/Empathy/FAQ#Audio_and_Video_calls"), I installed the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg

```

That's it. Restarted Empathy, managed to have videochats with gtalk users :)

---

### Post by tdkx89 on 2010-07-13
I can verify that errebepe's method works for me, too. Thanks a lot, dude!

---

### Post by YannBuntu on 2010-07-13
I am happy it helped you :)

> **errebepe said:**
> I installed the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg

```

Just for information, these 2 codecs (and many more) are included in ubuntu-restricted-extra. (I mention it because it is easier to install just 1 package, and because gstreamer0.10 may change to gstreamer0.11 one day ;) )

---

### Post by elidoperezmd on 2010-07-14
> **errebepe said:**
> I've got it working:

- Following YannBuntu's suggestion, installed Empathy from PPA:

```
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update
sudo apt-get dist-upgrade # I suppose "apt-get install empathy" works as well

```

- Then, following [Empathy's FAQ]("http://live.gnome.org/Empathy/FAQ#Audio_and_Video_calls"), I installed the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg

```

That's it. Restarted Empathy, managed to have videochats with gtalk users :)

Did all that, and it helped, thanks. But now empathy is not being managed by the little envelope, now is in the dock running by itself as any other program would, and not inside the evelope submenu....how do i drop it back in?

---

### Post by Soul77 on 2010-07-25
Hi,
Those who have managed to install ubuntu with empathy and google talk, could you advise what's the cpu usage?
Will it be all right to be used on a netbook with atom / celeron 900 processor?
 
I'm thinking of getting a cheap 2nd hand netbook for my parents for video chatting purpose only.
 
Thanks

---

### Post by fragos on 2010-07-25
I was using an AMD Sempron 2800+ 1.6 Mhz with a webcam.

---

### Post by Soul77 on 2010-07-26
Sorry. I mean what's the cpu % utilization (and what's your processor type) while doing the Gtalk video chat?

---

### Post by Soul77 on 2010-07-26
> **fragos said:**
> I was using an AMD Sempron 2800+ 1.6 Mhz with a webcam.
 
What's your CPU % utilization while video chat in the Gtalk?

---

### Post by fragos on 2010-07-26
> **Soul77 said:**
> What's your CPU % utilization while video chat in the Gtalk?

I upgraded to a new mobo with an AMD X2 245 so I can't help you there.

---

### Post by hempanicker on 2010-08-06
> **rcktsingh said:**
> I have been facing this problem since so long. Whenever I have to audio/voice call with my friends, I have to reboot my machine and go to Windows to use GTalk there. Sometimes gets frustrating !!](*,)

Isn't there any workaround for this ?
install windows on a Virtual Machine. It atleast saves the restart time :)

---

### Post by temporos on 2010-08-08
> **hempanicker said:**
> install windows on a Virtual Machine. It atleast saves the restart time :)
It kind of annoys me when people suggest running Windows on a virtual machine.  It's really a non-solution, since the whole point of Ubuntu (and Linux in-general) is to end our dependence on inferior operating systems, such as Windows.

---

### Post by krishnandu.sarkar on 2010-08-08
I never tried video chat. But audio chat works fine for me. But I need to call everytime. If the other person calls me, it freezes. What to do??

---

### Post by YannBuntu on 2010-08-08
> **krishnandu.sarkar said:**
> I never tried video chat. But audio chat works fine for me. But I need to call everytime. If the other person calls me, it freezes. What to do??

Install the following 2 packages : gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly-multiverse

If it still does not work, upgrade Empathy to last version , by adding "ppa:telepathy/ppa" to your Software Sources.

---

### Post by krishnandu.sarkar on 2010-08-09
> **YannBuntu said:**
> Install the following 2 packages : gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly-multiverse

If it still does not work, upgrade Empathy to last version , by adding "ppa:telepathy/ppa" to your Software Sources.

Thanks, I'll try that.

---

### Post by misGnomer on 2010-08-20
As mentioned [elsewhere]("http://ubuntuforums.org/showthread.php?t=979459&page=2"), the Big G has **finally** released a plugin (.deb) for [in-browser Google/Gmail video chat]("http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html").

It's h.264 and for x86 (intel/amd) only so no open-source and multiplatform (*) [VP8]("http://en.wikipedia.org/wiki/VP8") goodness yet, but it's a small step forward.


(* of course h.264 + Empathy IM et al has worked on multiple platforms for a while already...)

---

### Post by Dexter_Greycells on 2010-08-21
My initial problem was the camera on my Sony VAIO VGN-FZ210CE. Ubuntu did not have its driver and I installed it manually from the PPA [https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa) thanks to another Ubuntu forum post.

Cheese works with my camera beautifully but Empathy spoils the video that is broadcasted and seen by the user at the other end. The image is strangely split into two halves with one half reversed at 180 degrees! Then there is a lag in the movement too by around 3-4 seconds. And lastly. though the image is almost illegible you can make out that the level of zoom on it is just too high. Trying to see if there is a bug report for this else I will file one. Empathy should come with some video settings.

I know that Google has released an official plug-in but being a Linux user means getting things to 'work' anyhow!

---

### Post by Dexter_Greycells on 2010-08-21
Filed the below bug report - 
[https://bugzilla.gnome.org/show_bug.cgi?id=627613](https://bugzilla.gnome.org/show_bug.cgi?id=627613)

Will update the thread with the status of the bug report if anything fruitful turns out.

---

### Post by arinya on 2010-08-27
> **errebepe said:**
> I've got it working:


```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg

```That's it. Restarted Empathy, managed to have videochats with gtalk users :)

So, It can be concluded that empathy package has an incomplete dependence tree.

---

### Post by YannBuntu on 2010-08-27
for information: [https://bugzilla.gnome.org/show_bug.cgi?id=623339](https://bugzilla.gnome.org/show_bug.cgi?id=623339)

---

### Post by Ballbrekr on 2010-09-18
very new to lucid lynx (all of linux for that matter).  What will work for making a video call?  Besides skype not sure if a can handle calling overseas.  Before i joined linux, it was MSN messenger through a hotmail account.  Now apparently, a sip server wont accept my account.  Any ideas?  Has anyone had any success with anything?

Very Respectfully,
Ball

---

### Post by fragos on 2010-09-18
> **Ballbrekr said:**
> very new to lucid lynx (all of linux for that matter).  What will work for making a video call?  Besides skype not sure if a can handle calling overseas.  Before i joined linux, it was MSN messenger through a hotmail account.  Now apparently, a sip server wont accept my account.  Any ideas?  Has anyone had any success with anything?

Very Respectfully,
Ball

Google Chrome with the Google Talk plugin for Linux to other Google users.

---

### Post by YannBuntu on 2010-09-19
> **Ballbrekr said:**
> What will work for making a video call?

If you want to do audio+video with Windows users, I recommend :
- Gtalk plugin (in Firefox, or Chromium, or maybe other web browsers..)
- Skype
- Ekiga

These 3 solutions exist also for Windows users. Only Ekiga is 100% open-source. 

On Ubuntu, Gtalk can also be used with Empathy PPA and restricted codecs.

---

### Post by kidguayas on 2011-01-27
My empathy is not sending video. I have tried to follow the steps:

sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update
sudo apt-get dist-upgrade # I suppose "apt-get install empathy" works as well
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg 

but I still can not send video. Any other ideas?

---

### Post by temporos on 2011-01-27
> **kidguayas said:**
> My empathy is not sending video.

[This]("https://bugs.launchpad.net/empathy/+bug/434878") is a known issue since Karmic.  It has yet to be remedied.

---

### Post by teamanx on 2011-02-12
I had the same problem, and got solved by adding the empathy/telepathy ppa:

```
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get dist-upgrade
```

Of course, you must also install gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-ffmpeg, as said two posts above.

---

### Post by egemenaydin on 2011-03-05
> **errebepe said:**
> I've got it working:

- Following YannBuntu's suggestion, installed Empathy from PPA:

```
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update
sudo apt-get dist-upgrade # I suppose "apt-get install empathy" works as well

```

- Then, following [Empathy's FAQ]("http://live.gnome.org/Empathy/FAQ#Audio_and_Video_calls"), I installed the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg

```

That's it. Restarted Empathy, managed to have videochats with gtalk users :)

I am using Ubuntu 10.10. I have done whatever said here and managed to connect using google talk. However, I reveive and send blurred video. Is there any soluton of that?

---

### Post by freechelmi on 2012-01-08
Just to say I just gave up using empathy for jabber Video chat: 

- Even between 2 lucid empathywith gmail adresses , it just fail saying it cannot link source.

- Connecting to Gmail plugin fails as well.

Finally the Gtalk-gtalk linux plugin works great but consume a lot of CPU

---

### Post by temporos on 2012-01-08
> **freechelmi said:**
> Just to say I just gave up using empathy for jabber Video chat
I gave up a while ago.  I gave up on doing anything with my webcam a while ago, actually.  Ever since I installed Lucid, using the internal camera went from bad to no-go.

---

### Post by minigilani on 2012-04-30
I know this is an old thread and all, but i just thought i'd let you know. I did a clean Precise Pangolin 12.04 install and Empathy handles Google perfectly now.
I do have ubuntu-restricted-extras but i get the feeling it would work without it too.

I have a few cosmetic issues with how the video window is seperate from the chat box, and how the video box always opens, even if i'm only in a voice call, and how it doesn't automatically close the video box after the call's hung up, and how it sometimes doesn't handle my Google status right, but, ehh.. it works!

---

### Post by YannBuntu on 2012-05-02
> **minigilani said:**
> I know this is an old thread and all, but i just thought i'd let you know. I did a clean Precise Pangolin 12.04 install and Empathy handles Google perfectly now.
I do have ubuntu-restricted-extras but i get the feeling it would work without it too.

I have a few cosmetic issues with how the video window is seperate from the chat box, and how the video box always opens, even if i'm only in a voice call, and how it doesn't automatically close the video box after the call's hung up, and how it sometimes doesn't handle my Google status right, but, ehh.. it works!

you should report these issues on the Empathy mailing-list: telepathy ATT lists.freedesktop.org

---

