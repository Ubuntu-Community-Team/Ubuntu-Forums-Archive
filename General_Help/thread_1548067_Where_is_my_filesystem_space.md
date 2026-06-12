---
title: "Where is my filesystem space"
date: 2010-08-07
forum: General Help
---

### Post by gauravbutola on 2010-08-07
I made my filesystem of around 150GB and My home folder has only 45GB of data.
Today I saw a warning (saying something like) "Your File system has low disk space 1.3 GB please delete some data"
then I did a disk analyzer using 'Disk usage analyzer' and I saw that it was saying that my file system is only 49.7GB, but when I see it from Disk utility, it says that filesystem(/) is 146 GB.

Now I have no idea how come its saying that i am running out of space. 

I am attaching a screenshot of my disk analyzer and Gparted. well my disk analyzer itself says that filesystem capacity is 133.9GB but shows / to be only 49.7
please see the screenshot.

---

### Post by gauravbutola on 2010-08-07
bump

---

### Post by gauravbutola on 2010-08-08
This is my 3rd question ever in ubuntu forum and I am so sad to see that out of my 3 question only one was answered (which was about linux not ubuntu).
I think I would never again come back here to seek any kind of help. yahoo answers is rather better where people atleast come to show there presence to ur question even if they are blank about that.

Bye to all.

---

### Post by worksofcraft on 2010-08-08
Actually I subscribed to your thread because I can see the same problem on my computer but I don't understand it either.

Attached is what my disk usage shows... well that is if I can work out how to attach a picture ;)

---

### Post by worksofcraft on 2010-08-08
Anyway I'll tell you my theory:
What it show is 100% is of what is used and then the others are percentages of that. You still have loads of unused disk space but the analyser is analying only the used disk space.

Does that make sense to you?

---

### Post by 23dornot23d on 2010-08-08
I think this partition table needs to be set up slightly differently ...

What computer is it that you use > > ? 

But its not a simple task .... from the way you have it currently layed out

If you want to go through it step by step - I will try to help you

What Operating Sytems are you currently on this drive ?

( I read your previous posts and am surprised that no one has helped you - we can remidy that now )

_______________________________________________________________________

Its probably saying you are running out on your home drive ..... you have loads of 

unallocated space and also - the one you have marked as backup .... hardly has anything on it

this could be resized and moved to the right .

________________________________________________________________________

If sda3 has little on it and you can copy this to a flash drive or somewhere else then :-

I would delete sda3 ....... resize sda4 ...... to use all the unallocated space ....... to its right

Then move it to the right to give more space for sda6 ...... but this is going to take a lot of time
as the 57 Gig partition would all have to be moved to the right ...... 

To allow more free room for sda6 .......

__________________________________________________

If it was me ...... ( to save loads of hassle - plus to remove any possibility of losing data )

I would buy another drive possibly a USB one ....

and add it to the system as the DATA is probably better left alone
a new USB drive gives you more possibilities and are cheap nowadays.

They are also very useful for backups .......

---

### Post by gauravbutola on 2010-08-08
First of all, I am glad to see that there are still people to help out others. thanks to all.

> **worksofcraft said:**
> Anyway I'll tell you my theory:
What it show is 100% is of what is used and then the others are percentages of that. You still have loads of unused disk space but the analyser is analying only the used disk space.

Does that make sense to you?

I also think the same, but in this case I should not get the warning that I am running out of space in my filesystem. the warning said that i only have 1.9 GB left in filesystem.

I am running lucid lynx.

---

### Post by 23dornot23d on 2010-08-08
The problem is you are only allowed 4 primary partitions
so that means as it stands ....  you cannot use the unallocated space
without joining up the unallocated space to an existing partition ....

These are the 4 main partitions .....

( sda1 sda3 sda4 then the extended sda2 )

Thats the 4 taken up so it allows no more ...... without re-organising the drive.

**Once you completely fill the partitions that are almost full then it gets very difficult.**

adding a new drive means that you can move some of the valuable data off this drive
onto another one ,,,, keeping it safe.

Then you can start to re-organise the first drive in safety ......

You can re-organize it as it is .... but it will take time and by that I mean hours to move 57 Gig of Data.
Unless someone else can see a better method ....... 

Oldfred is brilliant with this type of problem .... if he is around.

---

### Post by gauravbutola on 2010-08-08
> **23dornot23d said:**
> The problem is you are only allowed 4 primary partitions
so that means as it stands ....  you cannot use the unallocated space
without joining up the unallocated space to an existing partition ....

These are the 4 main partitions .....

( sda1 sda3 sda4 then the extended sda2 )

Thats the 4 taken up so it allows no more ...... without re-organising the drive.

**Once you completely fill the partitions that are almost full then it gets very difficult.**

adding a new drive means that you can move some of the valuable data off this drive
onto another one ,,,, keeping it safe.

Then you can start to re-organise the first drive in safety ......

You can re-organize it as it is .... but it will take time and by that I mean hours to move 57 Gig of Data.
Unless someone else can see a better method ....... 

Oldfred is brilliant with this type of problem .... if he is around.

But i dont see a point in messing with my other partitions because my point was that, I gave my filesystem around 150gigs and at 46gigs it says that I am running out of space. so I dont think this issue could be solved by increasing its size any further.

---

### Post by 23dornot23d on 2010-08-08
Look at the used and unused space ..... although you have 8 Gigs to work in at the moment ..... (the rest in Brown is all used space) ..... you have two partitions to the right ..... but they are not being used by the   / .... (root area) sda6

You also probably have this situation ([COLOR=Red] /[/COLOR] and [COLOR=Red]/home[/COLOR] in the same partition) therefore 7 gigs free on [COLOR=Red]/[/COLOR] and 1.3 gigs free on  [COLOR=Red]/home[/COLOR]

So when it runs out of space .. it gives a warning first ,,, "Your File system has low disk space 1.3 GB please delete some data"
It gives this warning before you fill it up completely ....... because then it gets more awkward to fix it,

The brown areas shown below ( is the area that your files already take up on the disk ) the white bits on the end are what you have left.

[IMG]http://i38.tinypic.com/k1pait.jpg[/IMG]


> 
But i dont see a point in messing with my other partitions because my  point was that, I gave my filesystem around 150gigs and at 46gigs it  says that I am running out of space. so I dont think this issue could be  solved by increasing its size any further.     
Do not get me wrong ..... but this is like filling a cup up with water ..... getting almost to the brim ...... 

and then saying but I have another empty cup in the cupboard - but I will not get it ......
  
So what will happen as the tap fills the cup ..... unless you bring it across and use it for the overflow.

Similar with the drive ..... if you do not bring across the empty space on the right ..... it will fill .... but with a computer it cannot overflow
so it may just stop.

___________________________________________________________

To keep filling your partitions that are almost out of space that I have arrows to the remaining space left on them
will end up with a difficult situation ..... unless you can get some space back.

Have you ever used these commands from a termlnal ... 

( Using these may get you a lot of space back if you have never used them before ... these will work in Ubuntu ...... )
[B]
sudo apt-get clean
or
sudo apt-get autoclean
[/B] 

The two areas to the right that I put red crosses through ..... cannot be used ...... 
  without some work to the partition - or removing some files / data and storing it somewhere else ....

unless someone else can explain a way to add it to the (root and /home partition) without doing  a resize 



The two partitions with red crosses through them on the right are like two empty cups .... 
sitting in a cupboard empty at the moment ......

They are there ...... but the System as it currently stands cannot use them - because they are
not added to the (areas / file system) that needs this extra space ......

Thats the best way I can explain the situation ........ I hope it helps in some way

---

### Post by gauravbutola on 2010-08-08
_A million thanks to '23dornot23d', u took so much of ur time to make me understand things, and kept me from loosing my reliance on ubuntuforums._

I was so much screwed up and I tried everything I could and I also deleted my sda3 and did autoclean (I used to do it before also).
today I rechecked my gparted and saw that the used space was changed.
I really have no idea what led to this difference in my filesystem's used space. i am attaching the todays screenshot of Gparted.

---

### Post by 23dornot23d on 2010-08-08
One more step will give you the unallocated space too .....

if you re-size the last partition sda4 ...... to the right ...... you can add more white to that one too
thats if you want to ....... *what is on sda4 > ? ...... is it a snapshot or a virtual system 
if so a re-size of that is probably not needed
(the grey unallocated is not used at all by anything at the moment.)

To make sda4 bigger ..... by increasing the size to the right of it ..... in gparted ... 
you can slide it across ....to the right ..... it may take a long time to do though as
it checks and makes sure all the data is good first ..... 

( or you can keep the unallocated for another system at a later date ....)

Ok its looking good and thank you for the kind words .... ;)

---

### Post by gauravbutola on 2010-08-08
Thanks for the suggestions. 
could you tell me what should be the size of filesystem if i create a separate home folder. and install 25-30 softwares.

---

### Post by 23dornot23d on 2010-08-08
1...... /home ......... is for all your data and documents ..... 
and the space you use for this type of data can be anywhere on the drive - so you can set a separate partition ,,, 
but it wont be /home (this usually needs to be set at the installation stage first before any thing else is put on)
 .....  so its no real problem having a data drive, but it will not be classed as part of your /home directory ..... it will be a separate partition .

You can use the unallocated space for any type of data ..... just format it as ext4 and then it will become a directory and you can drop things into it ........ from your other Linux Distributions. as long as they both have read / write access to it. 
( I do this sometime .... a type of share folder between two or more Distros)

2...... The size of all the software you are going to be adding ..... how longs a piece of string. * I really do not know .... 25-30 pieces of software .... this depends on there dependencies too ........

I can quite easily use 20 to 30 Gig for the programs that I add ......... you may have to let me know what you intend adding and I could make a better guess ......

40 Gig max for me would be quite sufficient for the Root ........ everybody is different here - it depends on what you intend adding ...... 

( A lot of 3D games would start filling it up ) but I guess you can always remove some
of these and replace with others - OpenOffice .... is quite big ...... JDK for Java is big .... Latex is big, development programs and QT4  etc ... )

You should be ok with 135 Gig for a long time as long as you split it around 50 . 50 .......... if you are not doing anything out of the ordinary.

DVDs and Movies ..... all can go in the spare partition .... 
Photos etc ..... I put these in two places always .... USB hard drive and the laptop drive.

---

### Post by gauravbutola on 2010-08-08
Thanks alot for bearing me. I think this thread should be marked as solved.

---

### Post by 23dornot23d on 2010-08-08
Ok good luck with whatever you decide to do ......):P

---

