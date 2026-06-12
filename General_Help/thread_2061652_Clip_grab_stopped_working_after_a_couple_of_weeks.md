---
title: "Clip grab stopped working after a couple of weeks"
date: 2012-09-23
forum: General Help
---

### Post by sofasurfer on 2012-09-23
I was using clip grab for a couple of weeks, then all of a sudden it will not download files anymore. I insert a URL and it is as if clip grab does not recognize it and the file type options remain inactive.
I tried googling the problem but it seems complicated to me. Can someone explain what went wrong and what I can do to make the program work again?
Thanks.

---

### Post by sofasurfer on 2012-09-24
:confused:

---

### Post by daslinkard on 2012-09-24
1st I would purge the entire clipgrab that you have on your system....t

Next you will run the following sudo commands:

```
sudo apt-add-repository ppa:clipgrab-team/ppa

``````

sudo apt-get update
```

then

```
sudo apt-get install clipgrab
```

---

### Post by sofasurfer on 2012-09-25
I hate to be a bummer but I ran those commands a couple of days ago. And I am sure that before I did I ran apt-get remove and then "clean". Hmmmmm. 
Please don't give up on me. I loved clip grab and I really hope to get it running again but I don't know where to start. I wonder if I started with an older version and then I may have upgraded to a bad version.

---

### Post by daslinkard on 2012-09-25
> **sofasurfer said:**
> I hate to be a bummer but I ran those commands a couple of days ago. And I am sure that before I did I ran apt-get remove and then "clean". Hmmmmm. 
Please don't give up on me. I loved clip grab and I really hope to get it running again but I don't know where to start. I wonder if I started with an older version and then I may have upgraded to a bad version.
So you purged the program?

---

### Post by sofasurfer on 2012-09-29
Sorry for the delay.
To the best of my knowledge I did purge the program.

---

### Post by daslinkard on 2012-09-29
What happens when you run 

```
sudo apt-get purge clipgrab
```

and then try the additional sudo commands?
```
sudo apt-add-repository ppa:clipgrab-team/ppa 	

```
```
sudo apt-get update 
```
then
 	 	```
sudo apt-get install clipgrab 

```

---

### Post by sofasurfer on 2013-04-15
I am having this SAME TROUBLE AGAIN! I enter a url and I get the little box that says "Can't retrieve video title". The above step do not help. I have been using clip grab all this time. I don't get it.

---

