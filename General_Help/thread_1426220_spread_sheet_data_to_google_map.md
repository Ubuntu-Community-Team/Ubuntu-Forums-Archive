---
title: "spread sheet data to google map"
date: 2010-03-10
forum: General Help
---

### Post by Silvernail on 2010-03-10
Is there an application that will take the data from an Open Office spread sheet and locate and mark each address on a map?

I've got a long list that I need to sort and locate by zip codes.

Thanks
Dave

---

### Post by BenAshton24 on 2010-03-10
I don't think that such a program exists. It would be relatively easy to write a script that could do it though. I've got some free time, so If you want I could write something.

I'm not entirely certain what you are looking for though... do you just want a bunch of placemarks on a google maps map based on a list of addresses?

---

### Post by Silvernail on 2010-03-12
Thats exactly what I need. Postal zip codes can cover several hundred square miles. While you can sort a spread sheet via any column, some of that information could be way across town and some down the street.

I would like to be able to look at a map and see that so&so lives just down the street from such&such.

Thanks
Dave

---

### Post by BenAshton24 on 2010-03-13
Hey again, sorry for the late reply.

I wrote something quickly that should be able to do what you're looking for. It's not going to win any awards for epic programming but it should be good enough. All you have to do is download the file, make it executable: (right click -> properties -> permissions -> check : Allow executing file as a program) and then double click it.

Under the File menu, you can save and open maps. You basically copy all of the cells containing addresses into the "addresses" text area and then all of the corresponding names/businesses/whatever into the "names" text area. You then click "plot addresses" and it should plot all of the points on the map. A demo screenshot is attached along with the actual program.

Hope this helps :)

P.S. If you want me to add anything else, or fix anything, just ask

---

### Post by oldfred on 2010-03-14
BenAshton24 great little program. I am trying to teach myself python and like to look at different ways of doing things. This is a great example of lot of things I did not know how to do.

---

### Post by BenAshton24 on 2010-03-14
> **oldfred said:**
> BenAshton24 great little program. I am trying to teach myself python and like to look at different ways of doing things. This is a great example of lot of things I did not know how to do.

Glad you liked it :) Although it's more of a hack-job than anything and it cuts corners in lots of places for the sake of getting it done in 20 minutes. For example, it doesn't check the map files to make sure that they will work, and if there are more addresses than names then it won't plot them.

If you need some good resources for learning GUI programming with python then [http://zetcode.com/](http://zetcode.com/) has some really good tutorials for a number of different toolkits in several different languages.

I actually noticed a rather big flaw, I hadn't put the text views in scrolled windows, so when you enter more than 4 or 5 lines of addresses, it starts to make the window bigger along with the text. I've edited my original post with the fixed program :)

---

### Post by Silvernail on 2010-03-17
I have a list of 296 names and addresses.
It appears that the program plots 10 then can not find the next 10 then plots 10 and can not find the next 10 and so on........

The error I am getting on the screen is 'address' not found.

Are we trying to cram too much into it too quickly?

Thanks for you help on this matter.
Dave

---

### Post by Silvernail on 2010-03-19
Any this thoughts on this?

Does there need to be a 2 tick sleep in there someplace. Allow things to settle down before going at it again?

---

### Post by BenAshton24 on 2010-03-20
> **Silvernail said:**
> Any this thoughts on this?

Does there need to be a 2 tick sleep in there someplace. Allow things to settle down before going at it again?

Sorry :S I've never used the Google maps API before and as usual I dived into it without actually reading the documentation properly and missing this bit of crucial information:
> Additionally, a status code of 620 will be returned by the geocoder if you query it faster than it can handle.
I've fixed the code and edited my original post with the fixed program. I've also cleaned up the code a bit and will add a loading bar to determine when the plotting is complete if I have time at some point in the near future.

Hope this helps :)

---

### Post by BenAshton24 on 2010-03-20
I've edited my original post again with the updated program which has some new features including a loading screen whilst it plots the addresses. I've also added better error handling so that it doesn't crash if you accidentally open an incompatible file.

If there is anything else that you want me to add, just ask.

Ben.

---

### Post by Silvernail on 2010-03-20
Looking good. Thanks for your effort.
Need to do a little debugging.

The first time I ran it, the progress counter got to 98% and hung with several of these errors listed.
> console message: [http://maps.google.com/](http://maps.google.com/) @45: TypeError: Result of expression 'response.Placemark' [undefined] is not an object.

The next time I ran it the counter stopped at 85%.
The next time I ran it the counter stopped at 90%.

Would the method I use to enter the data have anything to do with this problem?  I have the data in files and I load each file into 'gedit' or 'cat' it to a terminal and highlight > copy > paste

---

### Post by BenAshton24 on 2010-03-21
> **Silvernail said:**
> Looking good. Thanks for your effort.
Need to do a little debugging.

The first time I ran it, the progress counter got to 98% and hung with several of these errors listed.

The next time I ran it the counter stopped at 85%.
The next time I ran it the counter stopped at 90%.

Would the method I use to enter the data have anything to do with this problem?  I have the data in files and I load each file into 'gedit' or 'cat' it to a terminal and highlight > copy > paste

wow, sorry about that. :? The problem is that I didn't add an exception for addresses that cannot be found. I've fixed the program, and have added a more advanced error logging system, it should alert you of any problematic addresses after it has plotted all the ones that can be found.

I've edited my original post with the fixed program.

P.S. Sorry for all of these problems :S

---

### Post by Silvernail on 2010-04-03
I'm getting this error and the program crashes. I got it to work once right after you made the last changes.

> console message: [http://maps.google.com/](http://maps.google.com/) @45: TypeError: Result of expression 'response.Placemark' [undefined] is not an object.


Is there someway to trap these errors and send the data to a list to see what is the problem? Send them to the list not found since they need to be validated.

Sorry I was so long posting back. A stint in the hospital will alter your schedule and priorities.

Thanks for your patience. 
Dave

---

