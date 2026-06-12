---
title: "app for complet burning soln?"
date: 2011-04-07
forum: General Help
---

### Post by ClientAlive on 2011-04-07
Hi,

I was wondering if there is an app for linux that is a complete soln for burning audio and dvd? I'm a little confused at this point. I dl smplayer thinking this would do it for me and I've googled for information. So far, the only thing I see that seems to do everything in one app is gear pro and that's expensive! If there's any way, I'd like to avoid going through 2 or 3 diff apps (or worse) to burn something.

Thanks.
Jake

---

### Post by bodhi.zazen on 2011-04-07
There are several applications you can use from command line tools to graphical tools.

My personal favorite is k3b , it is graphical and about as reliable and versatile as it gets.

---

### Post by ClientAlive on 2011-04-07
I'll check that out. I don't know how I got on the path I am right now - but it has just seemed so convoluted. I'm sure I just haven't discovered the right tools (apps) available. Weird. I wonder then, if k3b does do everything from beginning to end, if I need some of the other apps I installed trying to accomplish my task? (Like DeVeDe, for instance - which seems to only convert and create the menus).

Thanks so much. I'll install k3b and see how it works.

Sincerely,
Jake

-------------------------------------

Ok, so it turns out k3b is already installed on my machine. Must have been included with the o/s. So I open k3b, insert a blank cd, click the button to start a new audio project and then browse to the folder that contains the audio files I want to use and when I go to drag one of them into the window to add it to the project I get an error message talking about the file type not being supported and how I can convert it if I want to. It's an mp3 file. They are mp3 files. Doesn't make sense.

Here is a copy of the body of that error message:

 p, li { white-space: pre-wrap; }  Unable to handle the following files due to an unsupported format:
*You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.*
/home/clientalive/Downloads/Mere Christianity - C. S. Lewis/C.S. Lewis - Mere Christianity - 1 of 8.mp3


Thanks for your help.

-------------------------------------------

[http://ubuntuforums.org/showthread.php?t=21044](http://ubuntuforums.org/showthread.php?t=21044)

This is what I'm talking about! I realize this post is from 6 years ago, but this guy seems to be describing one of the two obstacles I seem to continually face when attempting to do the simplest tasks. I've never (since I started using computers) been in a situation where I had to piece together so many different applications, each doing only a small part of the whole task (and it's not a big task/ not asking much to begin with). Or virtually be a computer programmer to hack and crack and lord knows what else to get those apps (apps - plural) to support anything but one file type or do some other, normal, thing - that is necessary to complete the task. This is ludicrous! What am I missing here? Because I don't see how a situation like this is even possible. If it weren't so frustrating it'd be funny.

Look, I just, just started using Linux. I've contemplated using Linux for years but never took the step before this because I had heard stories just like this. Now, it doesn't make sense to me why others who have been using Linux would go through this kind of thing on a regular basis and continue to use it. All this makes me think it must just be me. I'm sick of Windows and I'm really, really hoping to make a go of this. As it sits though, I'm having a really hard time. Is this how it is all the time with Linux? I mean, is this what I signed up for? Please help me understand!

---

### Post by bodhi.zazen on 2011-04-07
Hard to know the relevance of a post form 6 years ago. Although the behavior may seem on the surface to be similar, any application or bug would be very different after 6 years.

I think your problem is with restricted formats, see:

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

Also I think it depends on what you are wanting to do.

If you simply want to burn a mp3 to a CD, you copy the files, ie make a data CD.

If you want to make a music cd, or something that plays in a CD player, then you need to use the wave format.

So I think the "problem" is that you do not understand the various formats / codics and/or you do not understand the difference from a "music" cd (which would require a .wav) and a data cd (which can use a mp3 or any other format).

[http://en.wikipedia.org/wiki/Audio_file_format](http://en.wikipedia.org/wiki/Audio_file_format)

A music CD is used by a CD player. A mp3 or data cd is used by a mp3 player. Some CD players will play mp3 files, others will not.

When "ripping" a music CD one pulls the raw .wav file from the CD and converts it to a mp3 (or other format) to save space.

HTH

---

### Post by ClientAlive on 2011-04-07
I'm sorry badhi.zazen. It's prob not as big a deal as it seems. Its just that this is one of the things I've been working on doing (off and on) for about a week now. I mean trying to burn various things (be it audio or video). I've gone through several apps and always seem do end up with some kind of problems. Coming back to the task last night re-opened a more general fear that has been playing in my head for a while now - that is, whether using Linux (in general) is going to be this kind of experience all the time and with a lot of the things I try to do with it.That's what I was thinking about when I pasted that link in my previous response.

You see, I've always been used to an app just doing basically everything you need it do - right out of the box. I suppose I've had to look for a certain codec before but I don't think I've ever had to use more than one app to burn a cd or dvd. For me it's always been: put the blank disc in the drive, open the program, make selections to a couple settings and click the button. After a little while the job is done, the disc ejects and you take a marker and write the title or whatever on the disc. Done. Simple as that.

I guess what I'm refereeing to when I say using more than one app comes from when I tried to use DeVeDe for the first time a couple days ago. When I installed it I thought it would be like using Nero or something like that. That it would do 'everything' out of the box (and that was what I was looking for when I got DeVeDe). When I went to use it for the first time I found that all it really does is convert the thing and maybe add a menu. When I googled around about it I found a tutorial on burning dvds where the guy was talking about 3 different apps to eventually get the job done - and one of them was command line.

He said DeVeDe could be used to make the video file into something the player would support (convert it, add a title, divide into chapters, etc) but was terrible at making an iso. So he had you using a different app to take the output from DeVeDe and turn it into an iso. Finally he had you using some command line tool to burn the iso. That just seems really convoluted and extreme to me.

Now, last night, I try to use k3b for the first time and the first thing I find out is that it doesn't support one of the most common audio formats out there. A format that is widely, widely used by people and supported on almost any device (like mp3 players for example, or on a home or car cd player). When I looked into it a little I see people are talking about some library called libmad0 or something like that. I looked in my installed programs and found that it was already installed - that it had already been there (but this doesn't seem to be making a difference).

What took me back to this more general fear is that the instructions people were giving for being able to burn mp3 with k3b seem to be so technical. Command line this and command line that. Suppressing updates so libmad0 is not removed later, etc, etc.

Now I want to learn how to do more with command line. In fact, I'm reading a really good book on Ubuntu right now that addresses command line in one of it's chapters. I just don't always want to have to deal with something that is over my head right then when I'm just trying to get something done.

So I guess I sort of got off track a little. Yes, the issue, in its simplest sense, was to burn an audio cd but to burn it in a format I know will be widely usable to almost any device I want to play it in. A little bigger than that, it's not just burning a single audio cd on one occasion in my life. As the days go on I will need to burn all kinds of things, movie dvds, data, make iso images, etc. I really am hoping I don't have to go through all kinds of grief to do those things. And, finally, biggest of all, the concern that using Linux in general will be this kind of experience all the time and with everything I try to do with it.

Long post. I know. I have a habit of doing that sometimes.

Thanks again for your help.

Jake

---

### Post by ClientAlive on 2011-04-07
I think your right. Sorry. I guess I don't understand much about the topic at all and the things I thought I knew were mostly incorrect. Some of that comes from Windows apps that are out there. The way the controls are designed in a lot of them allow you to think you are burning an audio or music cd with mp3 files. All I really know is what I've picked up intuitively from using the Windows apps I've used and that seems to be wrong. Guess I'll have to do a little learning here.

Have a fantastic day sir. Thanks for your help.

Jake

---

### Post by bodhi.zazen on 2011-04-07
> **ClientAlive said:**
> I think your right. Sorry. I guess I don't understand much about the topic at all and the things I thought I knew were mostly incorrect. Some of that comes from Windows apps that are out there. The way the controls are designed in a lot of them allow you to think you are burning an audio or music cd with mp3 files. All I really know is what I've picked up intuitively from using the Windows apps I've used and that seems to be wrong. Guess I'll have to do a little learning here.

Have a fantastic day sir. Thanks for your help.

Jake

As with Windows, there is a learning curve with any OS. Windows makes things "easy" by hiding some of the technical details. It is "easy" as long as the graphical tools / apps work. If they fail though, many apps are closed source, so hard to fix.

In Linux, apps are open source, so although technical, there is often a fix available.

Pick your poison ;)

Honestly it takes about 4-6 months to become comfortable with Linux, depending on how much you use it.

Most people dual boot for a while, and fall back to windows when they reach a dead end.

After a while you might find you boot windows less and less, and then one day you find you have not boot windows for 6 months.

People often ask me Windows questions (they think I know about "computers" because I am a Linux user), but honestly I have as much of a problem with Windows as you seem to have with Linux, I am just not familiar with anything beyond windows 2000 (and a little windows XP, emphasis on little).

Keep an open mind and ask questions on the forums.

But yes, most people do not know the gory details of audio / video formatting.

In my experience, K3b is about as easy as it gets for burning.

Linux is module, so if you need to convert a file, I like ffmpeg. It is command line, but very easy to user (for basic stuff) and lots of options (for more advance tweaking).

If you want a graphical tool, many people advise handbrake, but there are others as well.

This second set of tools converts mp3 to ogg or avi or whatever.

ogg is the 'open source' equivalent of mp3, it is compatible with web browsers (firefox) and most "mp3 players" will play ogg files as well.

This link:

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

Although very detailed and ffmpeg (command line) oriented was extremely helpful to me when I was learning the basics of avi.

There is a new av format, webm, which is an opensource replacement for flash. It works with any modern browser (firefox and chromium for example) as well as movie players (mplayer and vlc).

PM me if you want a link to a web page that uses webm (as a demo).

HTH and keep on learning.

The point of the forums is that we are not dry documentation, like a wiki or blog, we are a conversion (hopefully tailored to your needs). So again, if you have a problem, ask.

---

### Post by ClientAlive on 2011-04-07
Thanks bodhi.zazen. Wow! That's a lot of great leads for me to follow  and learn more. I have tabs opened to your previous post's links/ leads  and am reading on that too. I understand that the forum isn't designed  to be like a wiki but I get a little confused on how to approach getting  what I need sometimes. (I also am very appreciative of the help people  have been giving me here and have a strong desire to begin contributing  myself - just need to know enough to have something to say. For right  now I think I'll post something in Testimonials and Experience on what  I've experienced so far with this switch to Linux.)

I've been getting advice and hearing a lot about people dual booting  when they start out in Linux. Maybe I shouldn't be so stubborn but I've  chosen to be kinda hard on myself by not doing this and just jumping  straight in. On the one hand, I fear that having that crutch would  become a vice for me and end up being a stumbling block to progress On  the other hand, there are still things I need to do; and, when it comes  to that, I sometimes kind of freak out when it doesn't work as quickly  or easily as I would like. "Pick your poison" could certainly apply here  too.

By the way, I love your signature. It reminds me of something I read in Beginning Ubuntu Linux 5th recently:

"The name Ubuntu was a perfect choice to reflect both free software principles and South Africa’s
cultural heritage. Ubuntu (pronounced “oo-BOON-too”) is a Bantu word with synonyms in many
other African languages. Although it has been described as too beautiful to be translated into English,
the word reflects the idea that you only became truly human through other human beings. There is a
Zulu saying that goes: umuntu ngumuntu ngabantu (“a person is a person through (other) persons”). It
has also been defined as “humanity through others.” (p. 21)"

What a beautiful concept!

Oh, and, I was wondering what HTH stands for?

Thx

Jake

---

### Post by bodhi.zazen on 2011-04-07
HTH = Hope This (or that) Helps .

Dual booting can be less frustrating, but it takes longer to learn then 100 % switch.

It would be like quitting smoking (or other vices) - Are you the type to slow down and then quit , or go cold turkey ?

For me, for the most part, I went cold turkey with Windows (I made the transition in a week rather then a few months) with no regrets, but that may not work for you.

YMMV (Your Mileage May Vary).

I think the best way to use the forms is to participate, ie ask questions, people here will give you some good advice.

---

### Post by ClientAlive on 2011-04-19
Was just gong through some of my older threads and making sure I didn't miss anyone or anything I should have said.

I ended up going with k3b and love it. Thanks for the suggestions guys.

bodhi.zazen. It's been about a month and I'm loving my Ubuntu!  Learnin' to do all kinds of cool stuff with it.

Jake

---

