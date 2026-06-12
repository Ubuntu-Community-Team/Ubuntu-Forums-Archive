---
title: "How to set the timezone?"
date: 2011-05-29
forum: General Help
---

### Post by apollothethird on 2011-05-29
Does anyone know how to set the TimeZone in Ubuntu?

So far I find the command line: sudo dpkg-reconfigure tzdata

While on the service it looks simple, I'm sure there are occasion where people have serious problems as in my case.  I'm on a Holiday for a few days in a different timezone.  I live in Buffalo.  I know the area well and can easily see a city in the list that is close to where I happen to be and can choose America/New York.

However, in this case, I'm in Crestview, Florida and don't immediately know which of the cities in the list are representative of Crestview.  I want to change the time from UTC-4 to UTC-5.

I have spent some time clicking on some of the cities in Florida to see which one is going to give me the correct time of UTC-5 (an hour earlier than the time my computer clock is showing, since I'm coming from a UTC-4 time zone.

If knew which of those cities are closer to Crestview, it'd be easy.  But so for I haven't guested it correctly.

I can look at this list: [http://www.timeanddate.com/worldclock/custom.html?continent=namerica](http://www.timeanddate.com/worldclock/custom.html?continent=namerica)

And see cities that have the correct time Zone.  But the ones I'm seeing so far are not the same cities in the list from the time changing command.

At present I'm having to resolve to leave the timezone incorrect and subtract an hour from the time displayed on the computer.

There should be an easier way.  Thanks in advance if someone has any suggestions.

I know I can eventually keep testing the various cities in the list until I find one that will present the correct time.  But if I can learn a better way, especially a method of entering a UTC relative number such as UTC-5, it'd be ideal for the next time I'm visiting a city which I don't know the TZ location of the other cities close by.

Thanks in advance for feedback on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by wildmanne39 on 2011-05-29
> **apollothethird said:**
> Does anyone know how to set the TimeZone in Ubuntu?

So far I find the command line: sudo dpkg-reconfigure tzdata

While on the service it looks simple, I'm sure there are occasion where people have serious problems as in my case.  I'm on a Holiday for a few days in a different timezone.  I live in Buffalo.  I know the area well and can easily see a city in the list that is close to where I happen to be and can choose America/New York.

However, in this case, I'm in Crestview, Florida and don't immediately know which of the cities in the list are representative of Crestview.  I want to change the time from UTC-4 to UTC-5.

I have spent some time clicking on some of the cities in Florida to see which one is going to give me the correct time of UTC-5 (an hour earlier than the time my computer clock is showing, since I'm coming from a UTC-4 time zone.

If knew which of those cities are closer to Crestview, it'd be easy.  But so for I haven't guested it correctly.

I can look at this list: [http://www.timeanddate.com/worldclock/custom.html?continent=namerica](http://www.timeanddate.com/worldclock/custom.html?continent=namerica)

And see cities that have the correct time Zone.  But the ones I'm seeing so far are not the same cities in the list from the time changing command.

At present I'm having to resolve to leave the timezone incorrect and subtract an hour from the time displayed on the computer.

There should be an easier way.  Thanks in advance if someone has any suggestions.

I know I can eventually keep testing the various cities in the list until I find one that will present the correct time.  But if I can learn a better way, especially a method of entering a UTC relative number such as UTC-5, it'd be ideal for the next time I'm visiting a city which I don't know the TZ location of the other cities close by.

Thanks in advance for feedback on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
Hi, I do not know what version of ubuntu you are using, but you should be able to go to the top right of the screen click on the time and set the time and calendar from there.

---

### Post by Irihapeti on 2011-05-29
From the timezone map, it looks as though Florida is in the same timezone as any of the cities on the eastern US seaboard. Therefore you could choose any city on the east coast and it should give you the right time.

I think the precise location is really only important if you want the correct sunrise/sunset times and weather data.

---

### Post by apollothethird on 2011-05-29
> **wildmanne39 said:**
> Hi, I do not know what version of ubuntu you are using, but you should be able to go to the top right of the screen click on the time and set the time and calendar from there.

Sorry. I was kind of exhausted after a long trip (1100 miles).  I should have included more information conning my environment.  I'm running Ubuntu 11.04.  I also should have been more specific that I (while I'm anxious for any manner to easily see the current time) I was hoping for a cli resolution.  Using gui is okay.  I'm okay if there isn't a cli way of doing it.

While I was researching, I specified "cli" in my Google searchesl  I was sure there was a way using point and click, but at the time, I was looking for the word TimeZone in the various menus.  Then I went to Google.

The following command came up many times:

```
sudo dpkg-reconfigure tzdata
```After typing in that command, I thought I may have been looking at the screen that would come up if I used the mouse and point and click to get to the Zone change option.  In this case, it's a different screen and I can change it from the menu.

The dpkg-reconfigure tzdata command brings up a sent of places timezones of which I didn't know the relationship they have with Crestview.  I couldn't find the option to punch in Crestview.  Using the gui you gave me brings up a screen to actually type in the name of the City.

If my little city of Crestview were not significant enough to make it to the list of entries in the “Time Settings database”, then I could pick one of the larger cities in the area which would most likely be in the database.

It works perfectly and is easy to use.

Thanks again!

> **Irihapeti said:**
> From the timezone map, it looks as though Florida is in the same timezone as any of the cities on the eastern US seaboard. Therefore you could choose any city on the east coast and it should give you the right time.

I think the precise location is really only important if you want the correct sunrise/sunset times and weather data.

Thanks.  Hadn't immediately saw the map.  It works like a charm!

– L. James

– 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by wildmanne39 on 2011-05-29
> **apollothethird said:**
> Sorry. I was kind of exhausted after a long trip (1100 miles).  I should have included more information conning my environment.  I'm running Ubuntu 11.04.  I also should have been more specific that I (while I'm anxious for any manner to easily see the current time) I was hoping for a cli resolution.  Using gui is okay.  I'm okay if there isn't a cli way of doing it.

While I was researching, I specified "cli" in my Google searchesl  I was sure there was a way using point and click, but at the time, I was looking for the word TimeZone in the various menus.  Then I went to Google.

The following command came up many times:

```
sudo dpkg-reconfigure tzdata
```After typing in that command, I thought I may have been looking at the screen that would come up if I used the mouse and point and click to get to the Zone change option.  In this case, it's a different screen and I can change it from the menu.

The dpkg-reconfigure tzdata command brings up a sent of places timezones of which I didn't know the relationship they have with Crestview.  I couldn't find the option to punch in Crestview.  Using the gui you gave me brings up a screen to actually type in the name of the City.

If my little city of Crestview were not significant enough to make it to the list of entries in the “Time Settings database”, then I could pick one of the larger cities in the area which would most likely be in the database.

It works perfectly and is easy to use.

Thanks again!



Thanks.  Hadn't immediately saw the map.  It works like a charm!

– L. James

– 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
Your welcome.

---

