---
title: "Beekeeping Software for Linux"
date: 2011-10-21
forum: General Help
---

### Post by Mr. Beekeeper on 2011-10-21
I'm a beekeeper and I'm tired of waiting for a beekeeping mobile app / desktop program that suits my needs.  There are a few out there, but they either severely lack capabilities or are only for desktop / laptops.  (try typing in gloves covered in honey).  I would like to make my own app for Linux that would sync with the Android platform.  What I lack in knowledge, I'll make up for in hard work & determination.  

My question is this...

What kind of database structure should I learn that would be common between the two that would facilitate hive records?  

It would need to be:

a) able to be read by both systems

b) be expandable in fields (i.e. I might want to add color, weight, direction, etc. as time & programming skills progress)

c) Work in a way such that the GUI could interpret the data in different ways (i.e. the way music software sorts and shows, albums, artists, genres, etc.)  I would want to sort hives by location, size, health, etc.

d) I don't want to just "use a spreadsheet".


Thanks so much in advance.  The Linux community has always been great.  I'd love to be able to contribute.

---

### Post by 1clue on 2011-10-21
I'm a software developer, but I have no experience in Android or what works there.

I'm posting mostly to cheer you on and to relate a similar story.

Decades ago my sister opened a daycare.  Unlike most of the others in the city, she actually went through the government paper chase and did it properly.  She was licensed for 12 kids at one point.

Lacking software, she started playing with Microsoft Works and made a spreadsheet.  I stood by the sidelines and cheered her on.  With very few nudges one way or the other, she told me what her immediate objective was and I explained the choices available and what the advantages and disadvantages of each were as I saw them.  Her decision matrix was much different from mine, but she actually came up with a serviceable application that she was urged to sell commercially by everyone who saw it, including me and the state inspectors.  She never did.

This was in the early days of Windows 95.  Your Android device almost certainly has more raw computing power than her PC did at the time.


Getting down to the specifics of your application, what are you thinking?  A tablet or a phone?  Are you going to have some sort of honey-proof bag to put it in?

I would think that mysql is available on both.  It's a rock solid database.  I would focus on your data model first, then concentrate on the core functionality in a service layer, and then implement two separate user interfaces that access the service layer.

I imagine that your mobile app would only need a subset of functionality and the home app would use statistical tools that might be beyond the ability of a phone.  On top of that, the mobile app probably uses a different windowing API from the desktop.  Rather than trying to choose specific features to make one app work across both systems, you would be better off IMO to make two separate apps that each do what you want on the platform it runs on.

---

### Post by Mr. Beekeeper on 2011-10-21
Thanks for the encouragement!

>Getting down to the specifics of your application, what are you  thinking?  A tablet or a phone?  Are you going >to have some sort of  honey-proof bag to put it in?

I was planning on using a phone, & Otterbox does a good job of keeping the honey out.  

I guess I was looking for a common abstract form of database that both systems could read and write to.  I just didn't know the terms.  I've been thinking about what a beekeeping app should be for a long time.  I've got a lot of ideas that would be useful, I just will have to learn how to implement them.  

I did a little research and SQL is on both.  I'm going to have to read up on it now.  

Thanks!

---

### Post by 1clue on 2011-10-22
How big is your operation?  How many data points do you keep, what sort of things are you keeping track of?

I suggest getting all of your ideas into a cohesive whole.

Software design is not so much about storing a bunch of data as it is about making good use of the data, and organizing it in ways that the user finds helpful.

If you can break the task up into components, you might be able to design screens based on the individual tasks you're dealing with.  You don't want too many screens or you risk making your app unusable because of navigation problems, and on the other hand a single page app can make it unusable because of complicated screens.

What my sister did is focus on the one or two things that consumed the most time at any given point in the design.  A good application comes together organically.  If you design the whole thing at once you might wright what you thought you wanted, but then by the time you get done you'll realize that something entirely different is better.

Always focus on what makes your job better wherever you are when you're using that component.  Use the app as you work on it, make one feature that works really well and make the screen easy to use standing next to the beehive.

You might make good use of other tools on the phone to help you out.  For example, you could put a bar code or QR code on each hive in order to simplify data entry.

---

