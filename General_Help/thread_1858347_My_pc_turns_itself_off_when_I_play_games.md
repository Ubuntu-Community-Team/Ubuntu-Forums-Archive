---
title: "My pc turns itself off when I play games"
date: 2011-10-12
forum: General Help
---

### Post by colobix on 2011-10-12
Hey. my pc turns itself off for no reason when I play games.
Why is that? And is it possible to fix, or is the pc corrupt or something?
I use ubuntu 11.04 64bit.
The pc is also very loud and noisy right before it happens.
Any idea?

---

### Post by Basher101 on 2011-10-12
Sounds like an overheating of your CPU and it then crashes in order not to get fried...open your PC and try to get rid of any Dust on the CPU cooler and fans inside your machine. My old PC once got SO dusty, he would not even start up....

---

### Post by colobix on 2011-10-12
How do I do that? It's a laptop. I mean how can a laptop be dusty? Isn't it very compact in there?

---

### Post by Basher101 on 2011-10-12
that makes it alot more complicated...try cleaning all your exhaust holes of your laptop with a vacuum cleaner. Otherwise you must open up all your screws on the downside of your laptop, get the RAM modules out, unscrew even more...its a very loooong and hard process to open up your motherboard of a laptop....just try the vacuum cleaner and if that does not work, i suggest you give it to someone with technical expirience to do the throughout cleaning for you.

edit: how _old_ is your laptop?

---

### Post by colobix on 2011-10-12
Thanks. Yes I've done that already.
So there's nothing I can do? I mean change the CPU's temperature somehow?
I have no idea how to do that but I've read it's possible,
If I can get this fixed without paying for a techno guy to look at it, that would be great.

---

### Post by Mark Phelps on 2011-10-12
What you have here is a contradiction of terms ... you want to slow down your CPU to make it run cooler, but yet, you also want to play games -- which will automatically speed it up.  You can't have both.

If you find a way to throttle back the CPU to make it run cooler, the frame rate in games will then be so low as to render it unplayable.

---

### Post by MARP1961 on 2011-10-12
Try a can of compressed air from a computer store. The air inside the can is clean and dry. Just follow the directions on the can. I would imagine there are risks associated with putting a vacuum cleaner nozzle up to the vents. Is it possible that the fan could be forced to run backwards and cause high current to flow through motherboard components? Is it safe to use a vacuum to clean out computers?

---

### Post by mastablasta on 2011-10-12
it owuld be then best to find some "tech guy" or official service for this laptop. They might need ot apply new cooling paste on CPU, or you didn't clean it as good as you think you did. sometimes compressed air is used to clean it better from outside (vacuum cleaner doesn't have such small exhaust to be able to get it in there and clean it well. so you oculd try wiht compressed air can. or at service they usually have air compressors.
 
Another option is that one of the fans is not working propperly. still you would have to open it to see what is going on inside.
 
and make sure you are running on flat surface that doens't heat up too much.

---

### Post by mastablasta on 2011-10-12
> **MARP1961 said:**
> Try a can of compressed air from a computer store. The air inside the can is clean and dry. Just follow the directions on the can. I would imagine there are risks associated with putting a vacuum cleaner nozzle up to the vents. Is it possible that the fan could be forced to run backwards and cause high current to flow through motherboard components? Is it safe to use a vacuum to clean out computers?
 
yes i believe it is however i would not set it to maximum vacuum :-D
 
with desktop usually small suction is enough to pull the dust off components. But then again you can access them more easilly there.

---

### Post by Immolatus on 2011-10-12
What is the GPU in this machine? have you tried installing the proprietary GPU drivers? You can use the more robust drivers to scale back GPU performance to reduce temps. 

Th nvidia drivers are available through Ubuntu and the ATI Catalyst drivers are available for Linux on the ATI site.

Graphics cards produce the majority of heat in laptops these days. If heat is your problem, look there first. You may just have to live with slower a frame rate.

---

### Post by colobix on 2011-10-12
Thanks a lot guys.
I don't know about the GPU thing. How do I check that.?
The nvidia driver I use is the one from the "current" package.

But wait, an air compressor can for laptop? is that even possible? I thought that was a desktop thing.

Okay, before I send it to computer service, is it possible to make the cpu cooler? I don't care if the pc gets noisy as long as it will work.

---

### Post by Mark Phelps on 2011-10-12
If this is a desktop, then go back and reread post #8.  The answers you're looking for are in that post.

As to compressed air, we're talking about the spray cans you can buy at computer stores and office supply stores, that contain compressed air.

On a laptop, you stick the plastic tube into the spray nozzel of the can and spray air into the fan exhaust slots.  That will dislodge any buildup of dust and force it out the slots.

If it is a laptop, the compressed air is about all you can do -- unless you want to tackle taking it apart -- which I don't recommend unless you are experienced in doing that -- because laptops are real easy to break.

---

### Post by The Sorrow on 2011-10-12
GPU = Graphical Processing Unit ie. your Graphics Card.

---

### Post by colobix on 2011-10-12
@Mark Phelps I've said twice that I use a laptop, and not a desktop.

So how is that gonna work on a laptop?

@The Sorrow Okay. As I said, I use the "current" nvidia driver that came installed by default.
So, is that the best driver to not let the pc die when I play games?

---

### Post by cryptotheslow on 2011-10-12
> **MARP1961 said:**
> Try a can of compressed air from a computer store. The air inside the can is clean and dry. Just follow the directions on the can. I would imagine there are risks associated with putting a vacuum cleaner nozzle up to the vents. Is it possible that the fan could be forced to run backwards and cause high current to flow through motherboard components? Is it safe to use a vacuum to clean out computers?

The same risk exists using either a vacuum or compressed air. Whichever way the fan is made to rotate it will induce a current as it essentially becomes a mini-generator as opposed to a motor. Reverse current may be avoided in the power connection by use of e.g. a diode, same cannot be said for current induced in the "correct" direction.

Common wisdom is to physically prevent the fan from rotating when forcing air through it for cleaning purposes (make sure the machine is powered off first!). Doing this on a laptop is easier said than done of course.

---

### Post by MARP1961 on 2011-10-12
Many thanks for that cryptotheslow. I wasn't sure.

---

### Post by colobix on 2011-10-13
> **cryptotheslow said:**
> The same risk exists using either a vacuum or compressed air. Whichever way the fan is made to rotate it will induce a current as it essentially becomes a mini-generator as opposed to a motor. Reverse current may be avoided in the power connection by use of e.g. a diode, same cannot be said for current induced in the "correct" direction.

Common wisdom is to physically prevent the fan from rotating when forcing air through it for cleaning purposes (make sure the machine is powered off first!). Doing this on a laptop is easier said than done of course.

Okay so it's risky.
What other options are there that aren't risky?

---

### Post by mastablasta on 2011-10-13
no it's not risky. fan will turn as it is supposed to turn. just blow some air in from air can. it's not like you would be blowing gale force winds and for a long time. if that doesn't help, service is the only/best option when handing laptops.
 
yeah you cna make it cooler with various coolers (fan or watter) that you cna attach to bottom of computer. but i wouldn't recomend it until you are sure that all components function as they should. because you could increase the damage on hardware by doing that.

---

### Post by Mark Phelps on 2011-10-13
Since this appears to be a laptop, cleaning is really your only option.  Taking it apart to mess around with the CPU is very risk as there are fragile ribbon cables in laptops that are easy to break.

---

