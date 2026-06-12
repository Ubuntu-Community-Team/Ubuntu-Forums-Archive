---
title: "Does Linux just lack the basic feature of making programs quit before shutdown??"
date: 2012-08-23
forum: General Help
---

### Post by wolftune on 2012-08-23
On Mac, and I think on Windows too, when a user chooses to shut the computer down, each open program is told to quit. First and foremost this makes each program run its own internal quit routine. Sometimes this means bringing up a dialog asking about saving. This is basic good computing use. Linux seems to be lacking this entirely. Choose shut down, and BAM the computer is off, losing unsaved work and failing to just do normal quit routines. Users have to just manually remember to quit all open programs first&#8253; What am I missing&#8253; Surely this is a pretty basic idea that should have been standard on Linux for years. It's a real shame if this doesn't exist!

For reference, I'm using a KDE-based Ubuntu (KXStudio, specifically), but this issue is present on my parents' Mint installs and every other Linux system I've personally used.

---

### Post by Vaphell on 2012-08-23
i don't know what kde does but i just ran stock precise in vbox, opened gedit, modified empty doc, ordered shutdown. I got 'program is still running: gedit' dialog (lock/cancel/shutdown anyway) and another dialog from gedit, 'save file before closing?'

---

### Post by qamelian on 2012-08-23
> **wolftune said:**
> On Mac, and I think on Windows too,

Nope, Windows has the same behaviour as Linux in this regard.

---

### Post by hakermania on 2012-08-23
Hm, I am not 100% sure about this. For example, if you make an application with Qt, it never goes through its CloseEvent (which is the event that handles what to do on application close, like saving settings, removing temporary files and such) if you choose shutdown when the application is open. With this in mind, I suspect that an application (at least under Ubuntu) has to do something so as to hear for a specific system signal for indicating that shutdown is coming.

---

### Post by Capt'n on 2012-08-23
> **qamelian said:**
> Nope, Windows has the same behaviour as Linux in this regard.

Actually, it sort of does and sort of doesn't. While each program is shutting down, you have about five seconds (give or take) to click save which temporarily suspends shut down until the process is complete.  Otherwise, Windows assumes you don't want to save and shuts the program down without saving.

At least, that was how it worked on WinXP <snip>

---

### Post by wolftune on 2012-08-23
> **qamelian said:**
> Nope, Windows has the same behaviour as Linux in this regard.

Ok, well whatever. I've never respected or used Windows really anyway and don't care what it does. There's a lot of nice things about the Mac OS though, just enough problems ethically and freedom-wise that GNU/Linux is compelling.

So anyway, I'm not just asking for myself for KDE. I have my parents running GNU/Linux, and they are on GNOME-based systems and I plan to update their computers to the latest Ubuntu sometime.

It really shouldn't be the case that I have to worry about telling them to be careful to quit programs before shutting down. It's hard enough for them to learn to really be savvy computer users in any respect, and this seems like such a basic helpful feature.

Why can't there just be a command in Ubuntu that goes through executing quit commands on every program and then shuts down? If there were just a script that did that, it could be engaged instead of the normal shutdown command, and that's what I'd use, what my parents would use, and what I would push for being adopted as a default&#8230; why does it seem that nobody is thinking about this? I did try a search for this idea before posting here&#8230;

So, Vaphell, do you think it might be an issue with my parents on older versions?

Let me be more specific: I want to see Firefox bring up its alert that says "remember tabs for next time?" and I need Task Coach to do its unlock routine so it doesn't have an error when it opens next time. Currently, these things do not happen when shutdown is chosen on my KDE-based Ubuntu 12.04 nor on my mom's Mint 11&#8230;

---

### Post by qamelian on 2012-08-23
> **Capt'n said:**
> Actually, it sort of does and sort of doesn't. While each program is shutting down, you have about five seconds (give or take) to click save which temporarily suspends shut down until the process is complete.  Otherwise, Windoze assumes you don't want to save and shuts the program down without saving.

At least, that was how it worked on WinXP, the last OS I had from those leeches.

It actually depends on the application and whether or not the program is responding at the time. Most applications we use at my day job don't give you any warning, they just shut down. One notable exception is Outlook.

---

### Post by Zill on 2012-08-24
> **wolftune said:**
> ...Why can't there just be a command in Ubuntu that goes through executing quit commands on every program and then shuts down? If there were just a script that did that, it could be engaged instead of the normal shutdown command, and that's what I'd use, what my parents would use, and what I would push for being adopted as a default… why does it seem that nobody is thinking about this?...
I suggest it important to remember that Ubuntu, like all other Linux distros, is a *community* project.  There is no-one in overall control dictating exactly what functionality is, or is not, provided.  Ubuntu, quite simply, belongs to you, me and all the other users.

So, the short answer to your question is that if *you* require a particular function then it is up to *you* to implement it!  If you do not have the capability to do this yourself then it is necessary to recruit some assistance from developers with more experience.  Unsurprisingly, volunteer developers (generally unpaid) tend to work on what they want to work on.  Therefore we, as users, cannot demand this of them.

I suggest you promote your idea through the [Ubuntu Brainstorm]("https://wiki.ubuntu.com/Brainstorm/") system and see if more support can be generated.

[Post your idea for Ubuntu]("http://brainstorm.ubuntu.com/tour/")

---

### Post by wolftune on 2012-08-24
Zill, 

That is very fair, and I fully understand all of this. But I am at the stage of trying to understand the status quo and the history. It seems baffling that the worldwide community would have time and care for all the amazing features that GNU/Linux and Ubuntu already have and yet nobody would bother with this. It seems so basic. And it could certainly make a difference for novice users feeling happy with the system, never accidentally losing work, etc.

So, the question right now is:
Is this feature really hard to implement? Or is there already some utility made that does this but it hasn't been included by default for some reason? Or could it possibly be the case that most users don't care or haven't thought of this??

Based on one reply above, some aspect of Ubuntu does actually do this, but most people seem to be saying that it isn't really functional.

If I can wrap my head around the insane idea that of millions of users, I'm one of the only who would bother caring about this (I simply don't believe that right now), then I'll go about deciding whether to try to be part of making it happen. I understand the community-focus of all of this, and I love and respect that. I'm not some pissy consumer just harping on not getting what I want.

:-k

---

### Post by sffvba[e0rt on 2012-08-24
> **wolftune said:**
> That is very fair, and I fully understand all of this. But I am at the stage of trying to understand the status quo and the history. It seems baffling that the worldwide community would have time and care for all the amazing features that GNU/Linux and Ubuntu already have and yet nobody would bother with this. It seems so basic. And it could certainly make a difference for novice users feeling happy with the system, never accidentally losing work, etc.

Based on the amount of times someone has brought this up it doesn't seem to be an issue.


404

---

### Post by wolftune on 2012-08-24
> **not found said:**
> Based on the amount of times someone has brought this up it doesn't seem to be an issue.


404
Keep telling me that enough, and I will start to believe it. I am just truly surprised that this isn't something almost everyone would want and would have thought of&#8230;
maybe everyone just gets used to making sure to quit manually. It just seems like this would be a great step to making the system more user friendly and foolproof&#8230; just having the option of this behavior anyway&#8230; like maybe a new command called "quit open programs and shut down" as a choice besides just "shut down" ?

Besides my shock at this not being a popular request / idea, is there anything I'm missing about this being technically challenging or something?

---

### Post by amoun on 2012-08-24
Have you thought of using the hibernate option?

---

### Post by oldos2er on 2012-08-24
wolftune, I agree with you that programs should be shutdown cleanly when the system itself shuts down (yet another behavior that I miss from OS/2). I doubt if it's anything technical, but not being a programmer I can't say that with certainty. This seems to be one of those things that Linux simply does differently--not a satisfactory answer, I know.

---

### Post by amoun on 2012-08-24
1. Seems like it does sometimes.
[http://askubuntu.com/questions/168186/why-isnt-shutdown-giving-me-a-chance-to-save-files-in-running-programs](http://askubuntu.com/questions/168186/why-isnt-shutdown-giving-me-a-chance-to-save-files-in-running-programs)

2. There's the option of putting the computer to sleep, when closing the lid for instance, which will keep all files open, for restarting: awakening

3. There's hibernating, which will restore programmes to there place.

4. Then there's the option of closing without saving. This instant closing has the benefits of speed and not saving and cutting network traffic instantly, all which provide a type of security by disconnecting etc.

5. Then there are programmes that have the option to ask to save before closing as in the first case.

To have it ask if I want all open programmes saved would be a drag for me. Although ideally it should only ask where a file is being edited maybe, but that not the job of the OS more the job of the application, surely.

---

### Post by Kopkins on 2012-08-24
Personally I never found this to be a problem. Even if the computer prompted me for each program I have open, I would still prefer to shut them all down manually, which is what I do. But that is a rare occasion, I haven't shut down my computer in a little more than 8 days. Last time I did was to watch netflix on the Mac side of my computer. 

I get what you're saying about the user-friendliness of it though.

Kopkins

---

### Post by wolftune on 2012-08-24
> **amoun said:**
> 1. Seems like it does sometimes.
[http://askubuntu.com/questions/168186/why-isnt-shutdown-giving-me-a-chance-to-save-files-in-running-programs](http://askubuntu.com/questions/168186/why-isnt-shutdown-giving-me-a-chance-to-save-files-in-running-programs)

Ok, that's what I'm looking for! Could anyone tell me where to find more about when this occurs, which programs it does or doesn't work with, or what systems / versions of Linux this does or doesn't work on?
> 
2. There's the option of putting the computer to sleep, when closing the lid for instance, which will keep all files open, for restarting: awakening
3. There's hibernating, which will restore programmes to there place.

Well, sure, these are useful. Incidentally my 12.04 has hibernate removed (not by my choice), I think there was some issue with hibernate for some reason… I thought it was an issue with Ubuntu and the Linux kernel… But anyway, these are good for certain situations (most of the time really I guess)
> 
4. Then there's the option of closing without saving. This instant closing has the benefits of speed and not saving and cutting network traffic instantly, all which provide a type of security by disconnecting etc.

Sure, I can understand wanting this sometimes maybe.
> 
5. Then there are programmes that have the option to ask to save before closing as in the first case.
To have it ask if I want all open programmes saved would be a drag for me. Although ideally it should only ask where a file is being edited maybe, but that not the job of the OS more the job of the application, surely.

But I don't want all programs to be asking. What I want is less about asking to save and more about just making the program quit. For example, Task Coach does some short routine when the program is quit. There's no saving, no asking to save, but it does do some things (for one, unlock the file to allow other instances of the program to access it). I want the programs to quit themselves instead of just being forced closed.

---

### Post by mparillo on 2012-08-24
> **wolftune said:**
> Let me be more specific: I want to see Firefox bring up its alert that says "remember tabs for next time?" and I need Task Coach to do its unlock routine so it doesn't have an error when it opens next time. Currently, these things do not happen when shutdown is chosen on my KDE-based Ubuntu 12.04 nor on my mom's Mint 11…

I cannot speak to Firefox, and it might be application (or toolkit-specific) but I started to edit a file in kate, saved it, and made more edits. I then tried to shut down, and I got  a dialog box saying 'the following documents have been modified. Do you want to save them before closing?', just as you would hope for.

---

### Post by paichkash on 2012-08-24
some times i also fae this issue.. dont know why all behaviours are consistent in linux.. it seems most things were made in isolation .. and then someone just packed them in a single disc.. and each program has  unique interface and behaviour.. . ulike Windows..:guitar:

---

### Post by SeijiSensei on 2012-08-24
Most programs that I use ask the user to close unsaved tabs or windows.  I see this behavior in Firefox, Open/LibreOffice, and the GIMP, among others.  Konsole will sometimes prompt me if I have a remote SSH session running as well.  If a program doesn't prompt for user input, it usually means it can be closed cleanly in its current state.

Windows 7 prompts for open programs at the OS level, but in Linux it is up to the individual applications to determine if user intervention is required before closing.

I've used Linux for well over a decade and never found this to be a problem of any kind.

---

### Post by wolftune on 2012-08-24
> **SeijiSensei said:**
> Most programs that I use ask the user to close unsaved tabs or windows.  I see this behavior in Firefox, Open/LibreOffice, and the GIMP, among others.  Konsole will sometimes prompt me if I have a remote SSH session running as well.  If a program doesn't prompt for user input, it usually means it can be closed cleanly in its current state.

Windows 7 prompts for open programs at the OS level, but in Linux it is up to the individual applications to determine if user intervention is required before closing.

I've used Linux for well over a decade and never found this to be a problem of any kind.

Ok, thanks! Truth is, I had enough experiences of just choosing shut down and BAM the machine is off that I didn't keep testing. So in principle, if a program fails to ask or to do its routine, I could discuss that with the developer of that program. Right? And if a particular Ubuntu-based system isn't doing this at all, then it probably is something odd about that install?

---

### Post by black veils on 2012-08-24
what i have previously read was that if the system had more of a delay for the shutdown process, then the apps get a chance to cleanly close. i had issues with firefox, which is how i found that sort of information, but your thread has made me wonder. basically firefox didnt have force-close issues on one or 2 systems i used, but did on others, i thought because it is a speedy desktop, not giving things like firefox time to close properly.

---

