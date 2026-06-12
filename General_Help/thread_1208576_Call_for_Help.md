---
title: "Call for Help"
date: 2009-07-09
forum: General Help
---

### Post by marianlibrarian on 2009-07-09
Hello,

I am a library director in Geneva Alabama. We currently have 5 public access machines. Three are running Ubuntu 8.04 and two are running 6.?? Dapper Drake.

During the first two years. There were very few problems with hacking or abuse to the computers. But beginning in October of 2008, I began to observe people messing around with the menu bars and removing items or adding items. I attempted to ask for advice in the "Security Discussions" section and the answer I was given:
> My original thread:
I am having a hard time understanding how authorizations and privileges work for users. I have myself set up as an admin user in the admin group. Then I have patrons set up as patron in the patron group.

I just recently read a thread that said to make sure that users are in their correct group. I originally did not have any user assigned to any group.

I need to limit the patron group so that this user cannot move the panels or have access to the majority of menu items found under the System menu. It would be nice if I could remove the Administration menu item from the Patron user's menu, but still have it available when the Admin logs in.

I found something called ubuntu-tweak and installed it. It is nice but it is added to the Applications / System Tools menu. I tried to block this from user Patron by going through Authorizations from the Administration menu. But this item is still available to the Patron user. It doesn't even ask for their password. 

I have also explored Pessulus and liked it. But again this item is available from the Administration menu.

I know many have suggested Kiosk setup. I am desperate right now. My summer reading program is getting into full swing and I am by myself in this endeavor. I won't be able to learn and apply myself to a Kiosk setup until July or August.

Could someone please explain how to properly set up a user and how to limit access to menu items such as hiding the Administration Menu from the low level user.
> If you are having problems, rather then starting multiple threads and asking for step-by-step guides, please tell us what specific question you have. Please be sure to tell what guide you are suing an which step is problematic.
Then:
> The last piece of advice I can give you is to step back and consider if this is feasible for you right now. From your posting style it sounds as if you are taking on more then you can manage right now. Ubuntu is not a drop in replacement for Windows and it will take you time to learn a new OS. By that I mean you had to re-install to fix a problem with the way panels were set up (in a previous post) ? Fixing panels is a very basic task and while re-installing is a solution, it is obviously unrealistic.

I am not trying to be rude, just bring you back to reality.

Personally, if you are going to be responsible for managing these machines personally, you need to first learn how to run Linux. Then roll out the project for others.

Here is my reality. From 2006 - 2009 our computer use has increased by 406% our funding has decreased by 17% from the state, decreased 100% from our county (they didn't contribute much anyway) and our city funding has remained the same for about six years. There are 2 full time workers (including me) and 1 part time worker (19.5 hours per week only). 

I wish I could step back and evaluate for just 5 minutes! That would be a vacation - I haven't seen one of those in a few years.

Anyway, this guy whoever he might be, is correct. I barely have time to get simple library work done these days. I need help. A guy came in about two weeks ago and left me a note with contact information. He said that he is an expert in Ubuntu. But I lost the note. 

... and our roof was damaged from a wind storm this past Sunday and our library has been leaking inside.

I wish that someone could come here and just sit with me and show me how do set up a workable network. I have clicked on all the links and downloaded so many documents and read so many threads some nice some not and just tried to assimilate all this information to the point of tears.

If nothing else... is there an "Ubuntu for Dummies" book???? or an "Ubuntu for Profound Idiots" book?????

Edit: I am in the bottom south east part of Alabama. Our city limits are on the state line of Alabama and Florida. Perhaps there is a Florida forum?

---

### Post by retiree on 2009-07-13
Have you tried going to the main Ubuntu forums? ubuntuforums.org
I love Ubuntu but I'm not familiar with your problem. There should be someone on the main forums that can help.Hope you get it worked out.

---

### Post by marianlibrarian on 2009-07-13
:confused:
> Have you tried going to the main Ubuntu forums? ubuntuforums.org
I love Ubuntu but I'm not familiar with your problem. There should be someone on the main forums that can help.Hope you get it worked out.
I thought that is where I was?
:-s

Darn. I was hoping for human bean help but maybe a good book will do. Funny a librarian would say That.

---

### Post by retiree on 2009-07-14
You are at the state level. If you go to the main forums you can search for help on networking and wireless, and I feel like you can get some help there. You will have access to people all over the world there. There are plenty of people willing to help you. I do think you need for someone to help with your problem personally though. Maybe somebody knows someone willing to come and help you. Keep trying and don't give up and you will succeed. I know how frustrating it can get but, in the long run you will have learned more about Ubuntu. Regards, Clayton

---

### Post by martinbaselier on 2009-07-14
Where to begin? You have setup the pc's properly years ago. But that is not much help now. I'm using a different desktop, which means a different graphical interface, so I can not always tell the exact names/positions of things.

The most immediate problem is your network problem. I presume it's a standard install with network-manager installed. It should be in the menu.
With it you can setup the network. I don't know how your network is setup though. 

Normally you would have a dhcp-server somewhere, who gives an ip to the computers requesting it. So just telling it to automatically retrieve an ip, should normally do the trick.

Next the user-issue. In the settings, there is also an option users/groups. I presume you have a user admin and a user patron?
Just remove all rights from the patron user to begin with and make sure the admin has a good password. A good trick is using the first letters of a poem. 
Example:
Tiger, tiger, burning bright
In the forest of the night
would become:
TtbbItfotn

Next step, one of the items in the settings-menu is the menu setup, login as patron and remove all the items you do not want to be visible to the patrons.

The next step would be to make sure to strip the rights of the patron even further. Begin with almost no rights and then add the rights as they are needed. 

But since you already have more work than you can handle, and you still need to learn a lot, the best thing to do, would be to put up a note and ask for a volunteer to help. Apparently there are enough people who know how to mess up the system, so there must also be people who know how to prevent it, in your neighborhood. 

There are beginner books on ubuntu. I can't really advice you which one is good though, since I already had enough computer background when I started, I found it to be one of the easiest systems I've ever used. 
You might take a look at [this blog](http://amber.redvoodoo.org/). She started as a complete novice. I'd advise you to start at the beginning, and has some good tips for the beginning user.

The help is quite general, but I hope it will give you some starting point.

---

### Post by jonobr on 2009-07-14
Hello


I see a lot in this thread about permissions and so on.

Could you provide a pithy explanation of the problem?
Retiree you mention in the other post networking issues...
COuld we get a status update of what the current issue is,

Ill try and help as much I can, but again, recommend being concise as possible

Cheers


Additional- marianlibrarian, we all had to start somewhere, dont beat yourself up.
You are entering a huge world , its going to take a bit of time.

---

### Post by bekind2thenoob on 2009-07-14
To stop people messing up the panels...

Type Alt+F2 to bring up the run dialog. In this dialog enter

gconf-editor

and click run.

In gconf-editor in the left hand pane navigate to

apps > panel > global

and in the right hand pane check the box next to

locked_down

thats it you can right click the panel to see the results.

---

### Post by marianlibrarian on 2009-07-15
My goodness. Thanks for the replies. 

I have been reading as much documentation and posts when I have the chance. From what I can understand, a good plan of action would be to install Kubuntu on all the machines that are used for "public" access. Then install something called open kiosk. 

I downloaded Kubuntu 8.04.2 LTS. I realize that in October the next Kubuntu LTS will be available. I will deal with that then. I have downloaded Open Kiosk. 

I don't know when I will be able to work on one of my five public access computers. My part-time assistant's husband was rushed to the hospital yesterday and so I am very very short staffed for the next few days. 

My staff computers are running Ubuntu Dapper Drake. I will update them to Hardy Heron after I get the public computers done. 

If anyone sees something out of whack with my plan of action:
Install Kubuntu 8.04.2 on all public computers
Install Open Kiosk on all public computers
Sit down and take big breath

Let me know. 

Or if you see something missing in my plan for the public computers let me know or if you are NEAR Geneva Alabama let me know! :)

---

### Post by jonobr on 2009-07-15
Hello

Couple of points...

I have not worked a lot with anything other then ubuntu itself, however,
scanning around the forums there appears to be a lot of posts regarding people setting up the likes of internet cafes and so on.
SOme posts present experiences shared and may be worth a read.

[Here]("http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe")is a good example of people disccusing merits of complete access to total lockdown.

The initial thinking for the person in this post was to run edubuntu,
but that appears to be more child/ young adult orientated, and eventually they get around to your way of thinking.

The Kubuntu solution showcases the KDE environment and I believe there is an inbuilt 'kiosk' function in there.

[Here ]("http://developer.kde.org/documentation/tutorials/kiosk/index.html") is information on that, although scanning through it, it may be heavy reading.
 
ON the version your thinking of , going from Dapper to Hardy,
You may have noticed that the versions are given a number and an animal.

Dapper Drake
edgy eft (man this was horrible)
feisty fawn 7.04
gutsy gibbon 7.10
hardy heron 8.04
intrepid ibex 8:10
Jaunty Jackelope 9:04
Karmic Koala (which is in testing) 9:10

The one your on is LTS and the one your planning to go to is also LTS.
I dont know if you planned this because of it, or if you just liked the names?:-)
LTS is long term support and means canonical intend to support that release on desktops for 3 years and on servers for 5.
It also means you can purchase paid support , but why bother when you have these great forums.
You could go to a later version, but newer versions are introduced every 6 months or so and this usually means older ones will be made obsolete.
Using a newer version, makes you an early adopter, meaning your on the leading (bleeding) edge of new design and development which is a good and bad thing.

Also, to sound "in the know" people just use the first word in the release,
i.e. Im on feisty, or edgy was POC.

What I recommend is taking it one step at a time.

Just do one machine, or if you want to kick the tires first, and if you have a beefy enough windows machine, you could install wubi, which installs ubuntu  as an application on your windows machine, not an OS.

Your windows machine will be unaffected, but you will get to see what your considering.

One last point,
Majority of people on these forums, generally contribute for altrusitic reasons.
They get a strange kick out of helping other people.
If you start reading about opensource (i.e. how your getting these releases for nothing) and GNU you will understand some of the reasons why people do it.
You are going to run into jackasses (thats not an ubuntu release BTW)
who expect a lot out of posters,
however, heres a couple of points to note on posting which hopefully will mitigate that (mind you a thick skin is always the best)

- Keep it pithy (unlike my response here!!)
- Explain your setup when your asking a question.. ie versions and so on. People sometimes put it in their signature
 - If you researched your problem then indicate that saying, I found this link here but it did not work, or I saw this post etc.
- Dont be afraid to bump( i.e. if noone answers, especially in the most used threads, then you can put your post at the top by putting in a comment, (the word bump in the thread indicates that you what to "bump up my post"
- Try to post in relevant places, if you post in Absolute beginner, thats ok, but thats a busy thread and your post goes down the order quick. So if your having network issues, then post in the networking section as they move slower.
 - No harm saying your a noob (newbie at linux) people tend to explain things and are more patient.
- Try not to say things like, "If I dont get this working, im going to have to switch back to windows." People get annoyed by that, and some consider it a coercion to help them in their problems/
- Try to put in a relevant subject in your posts, putting in help, or what am I doing wrong, always draws peoples comments. 

Thats all I can think of for now.

Happy posting and hope you get setup there


Cheers

---

### Post by jonobr on 2009-07-17
marianlibrarian you have gone quite all the sudden.

Just wondering how your getting on

Cheers

---

### Post by marianlibrarian on 2009-07-20
It is one of the perks of being a librarian in a rural area - no resources - except for - self. I would distinguish myself as being from the deep deep southern US but this lack of resources in public libraries is... Nation Wide - probably world wide.

I am currently - as soon as I finish this - writing a letter to our governor asking for 5 grand to get some new computer furniture and other accessories. My computer desks right now are being held together with wood glue and now that is starting to fail. And our computer chairs are about 15 years old. It is not a good thing when your chairs are NSFW.

There is a bunch of other stuff but if I mention it, I will be unpithy? unpithworthy?? I have seen that word pithy in several places and it seems to mean --- verbose?:confused::o

---

### Post by QIII on 2009-07-20
> **marianlibrarian said:**
> 
Darn. I was hoping for human bean help but maybe a good book will do. Funny a librarian would say That.

One hopes that help from human beans is to be found here ... aside from the occasional jerk.

Don't be put off if someone says "Read this..." or "Look here...".

Sometimes it is callous, to be sure.

But generally it is an indication that the depth of the subject does not lend itself well to a piecemeal back and forth on a forum.  

Sometimes the right (and most helpful) answer is a redirect to another source -- with some expectation on your part that you should be able to come back here for help understanding some difficult detail without running into a jerk that sniffs at you for not understanding.

I don't know that the Ubuntu Pocket Guide (which can be downloaded here:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  ) would be in-depth enough for what you need, but it is free.  You may wish to purchase a copy of Ubuntu Kung Fu.  While it is a bit dated (Fall 2008 ) for Jaunty (9.04), it is certainly just right for 8.04 LTS (which I might recommend for your purposes anyway).

I invite others to give you more suggestions for reference material that might be more directly appropriate for your situation in addition to the "look here" links (which are helpful and worth a read.)

Someone suggested "bumping" your thread.  You can do that by simply adding another comment to it and just type "Bump".  But don't do that any sooner than 24 hours after your last post, as that is considered to be poor etiquette.

You might also consider creating a new post in the Security forum at [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338).  The folks who haunt that forum my be able to point you in the direction of more resources.

I hope you do not feel uncomfortable being a "noob".  We all were once.

---

### Post by jmszr on 2009-07-20
marianlibrarian,

There is an article starting on page 18 of full circle magazine, issue 7 : [http://fullcirclemagazine.org/2007/11/29/issue-7-released/](http://fullcirclemagazine.org/2007/11/29/issue-7-released/) about the Howard County Library and it's use of Ubuntu. There is a contact e-mail address at the end of the article - perhaps the librarian there can be of assistance.

---

### Post by QIII on 2009-07-20
> **jmszr said:**
> marianlibrarian,

There is an article starting on page 18 of full circle magazine, issue 7 : [http://fullcirclemagazine.org/2007/11/29/issue-7-released/](http://fullcirclemagazine.org/2007/11/29/issue-7-released/) about the Howard County Library and it's use of Ubuntu. There is a contact e-mail address at the end of the article - perhaps the librarian there can be of assistance.

Bravo!  +1

---

### Post by jonobr on 2009-07-27
Hello


That would be me guilty of the pithy comment.
That was more to do with posting technical issues to a wider forum.
So unpith (????) away.

I actually had a read of your story and found it truly inspiring.
Also about how your ubuntu vs xp side by side test on different hardware.

I would love to tell canoncial and these forums about the strides you have taken to use ubuntu in your library.
These are the stories people like to hear.

I also downloaded an audio interview you did, not sure where I got it, but your accent rocks!!

Major Kudos for the work you have done and I hope you get the money.,
I doubt you will , but you never know!!

Cheers 

Jonobr

---

### Post by marianlibrarian on 2009-07-30
Oh My Stars! I can't believe that interview is still out there. I have an accent?!? :)

I read the article that someone posted earlier on this thread. I was kind of encouraged by their story. At the beginning it states: 
> "We got interested in Linux because two of our IT guys (former Unix administrators) were big fans."

They had TWO IT people!?!?!?! Former Unix administrators!!!!!

To be honest, the article made me want to cry. But only for a few seconds. Then I got over it. I may not have the sophisticated setup this library has, but I did it _all alone_ with no prior experience in Unix or Linux. 

I sometimes threaten to give up and go back to windows but I have invested too much sweat equity into this venture. 

What hurts me most is the lack of documentation on third party applications. I am so close to getting Open Kiosk 2.0 to work. However, it asks me for information and I have no idea what to put in the blanks. 

I wish I could just be an IT person and get this done. But I am also a librarian -- in a small under-funded rural library - as a librarian, I wish that I could just work with books. But the floors have to be vacuumed or mopped and furniture dusted and toilets cleaned and ... take apart shelves from 1970 and put in some of the prettiest NEW metal shelves ever in my children's room!

:KS Anyway, today is a new day. Maybe today I figure it out and move on to the next project. Thank you for your kind and encouraging words. It really helps to know that someone is thinking about me that way. :)

---

### Post by jonobr on 2009-07-30
> . I have an accent?!?

Actually , Im an Irish guy moved an living in Ca working for a Chinese company which does most of it work in India, so everyone I deal with has an accent, so dont put too much stock in what I say.

> but I did it all alone with no prior experience in Unix or Linux. 

Major Kudos, and again, thats what makes your story noteworthy and inspirational for Linux fans.

> I sometimes threaten to give up and go back to windows 

Thats a common thought for desktop users, and you are going beyond what a desktop user does. You are also doing something people went to college for years to do, so try not to be hard on yourself.
One other thing , if you post a technical question, make sure not to say
"If I dont get this solved, im going to have to go back to windows" that will undoubtedly draw Ire.

> What hurts me most is the lack of documentation on third party applications. I am so close to getting Open Kiosk 2.0 to work. However, it asks me for information and I have no idea what to put in the blanks.

Agreed on the doc thing, on the questions, dont be afraid to post those questions in the main general help or desktop sections of the forums,
or if you not sure, drop me a private message. You can do that by clicking on my name and it has an option to send a private.
Try not to suffer in silence

> I wish I could just be an IT person and get this done.

Hopefully the forums can help you with your questions,
I do know having a person you can just tap on the shoulder to say, get this done, is the best but failing that, hopefully this space can help

Best of luck

---

### Post by marianlibrarian on 2009-08-05
The link to the Howard County Library was the direction I needed to go. But I was intimidated by the story because they had a whole IT department and this IT department had former Unix administrators. I was just a small town rural public library director. I have been humbled so many times in technical forums. What did I know?

I had tried something called Webconverger. It is still in development and did not meet my needs. But in my conversations back and forth, someone mentioned Groovix. This was the same thing that was used by the Howard County Library.

So I found the Groovix website and called their number and...

That has brought me to Today! In the space of 1.5 hours, I was able to bring back to life three public access computers in kiosk mode. Two are running from the DVD and one is running from Groovix on the hard drive. The difference is speed and also there are a couple of settings that don't get saved after reboot from the DVD - the printer and the session timer which is set for 30 minutes and I need 60 minutes. 

I went back and read the article about the Howard County Library and found that it was indeed Groovix that solved their problems. They had something like 300 public access computers to take care of. THAT is intimidating. Groovix uses Ubuntu. So everything was so familiar behind the scenes. 

I have already had several patrons come in and congratulate us on getting all of our PACs (public access computer) on line.

I would like to post a new thread, with the proper search key terms, to let other people in my situation know that this can be done. But I don't want to cross post - that has gotten me in hot water here a few times. :o

---

### Post by jonobr on 2009-08-05
Hello

If you look under the other forums section, there is a tutorial and tips section as well as a experience and testimonial section.

Im thinking either one may work for you, you could always link back to this post to show the work you have done to get so far.

I think if you were putting your experience down for to educate and help others, no-one would have a gripe with that!!

Congratulations and the thanks for sharing your experience.

---

### Post by retiree on 2009-08-05
Congratulations !!!  :popcorn:

I knew you could do it. Regards,Retiree

---

### Post by DrFrost on 2009-08-07
Hi. Just came across this thread and got sucked in. I don't know enough to really help, but thought I might put in a couple of thoughts about your setup...

First thing is security... *once all the dust settles* and you can take a step back and look at your awesome setup ;) it might be a good idea to check your network for vulnerabilities... I would recommend something like running Nessus (which you will have to install from Add or Remove) and if you're in a pinch for time or if you are unsure of what's up let us know.

Secondly, when I started transitioning to Linux, one of my stumbling blocks was the issue of still needing certain Windows-only programs. Since I telecommute for work, this was a serious issue. I found VirtualBox (which, again is available from add/remove) took all of the sting out of transition. I don't know if that would apply in your situation, but it was part of my successful strategy. It might at least take some of the sting / urgency out of various points of your migration.

Good luck!

---

### Post by marianlibrarian on 2009-08-07
So far so good... It has been 2 whole days.

All systems go and the natives (patrons) are happy :D

School began here today, so this afternoon will be our first after school crush. We will generally have between 35 and 45 patrons using our 5 computers each day. 

I am feeling better now. The past year has been a pure horror for me. Trying to keep our bathrooms and computers in order and just do regular librarian work and have a successful summer reading program has been more than I could do. Unfortunately, resources dried up and I have had to deal with a few very mad and unhappy patrons. 

They were only a few although very loud complainers. They also are not from Geneva. I guess they are used to better amenities than what we have to offer. I can only hope that they go back soon to this place that is so much better than here.:lol:

---

### Post by marianlibrarian on 2009-11-06
):PI have a "few" minutes and wanted to stop by and let you know that .... all 5 of our public access computers are functioning wonderfully using Groovix. I have only had ---- one ---- patron complain. All he said was that he didn't like the way it looked. I simply smiled and said nothing. He has no idea of the mind bending dog cussing time I have had over the past year.

Oh and I have a new roof but not before the workers left part of it uncovered Friday October 9th and of course we had a down pour that night and yes... it poured in the library. 3000 books had to be moved and ServPro  cleaned it up and then 3000 books had to be put back. The roofing company bless them acknowledged the mistake and have taken care of everything. I only lost six books out of the 3000. - amazing. As of yesterday, the ceiling tiles and insulation have been replaced and now it is back to .... normal?

Never Ever a dull moment!

---

### Post by jonobr on 2009-11-06
Man, your really having a bad year.

As for the one customer, you get those everywhere,
I would have asked him if he purchased his prepaid data usage card before using the machine.
When he responds and says, "No, I didn't think I needed one"
I would respond with " exactly........your welcome", 
but you are free to put in any expletive laden comments here!


Ciao and again, congrats, your an inspiration

---

### Post by jmszr on 2009-11-06
Madam Librarian...Marian,

I've been keeping an eye on your continuing efforts and travails - it seems like you have to have covered about all of Murphy's Laws by now. It's good to hear that things are back to "normal" (I think). As for your unimpressed patron - meh, there's one in every crowd.

Best Wishes for an uneventful New Year.

---

### Post by marianlibrarian on 2009-11-06
:lolflag:
When I was a kid, my parents watched Hee Haw (a television program that I think was produced in Nashville TN). Anyway, it was silly and appealing to me as a kid. One of the regular skits they did was about bad luck.

[FONT=Comic Sans MS][SIZE=5][COLOR=Red]If it weren't for bad luck, I'd have no luck at all. Plum despair and agony on me.
[/COLOR][/SIZE][/FONT]
The use of the word "plum" has nothing to do with fruit. I have heard it used like the song uses it all my life and I think you could probably substitute the word total but that would mess up the song.

But now I am thinking about all the things that have happened to us this year. The roof and the leaks and the hair pulling computer problems were just a few of the many interesting things that have happened only this year. Beginning with the guy who drove through our community and shot and killed 10 people in March 2009. I'll save the list for later. Too much shooting and killing this year. Too much.

Anyway, thank you so much for the kindness and support that I have received on this forum. You really are the best!

---

