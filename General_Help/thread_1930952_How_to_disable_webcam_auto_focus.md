---
title: "How to disable webcam auto focus?"
date: 2012-02-24
forum: General Help
---

### Post by boblettoj99 on 2012-02-24
Hello, I am running ubuntu 11.10 and I would like to disable the auto focus of my Microsoft Lifecam Cinema webcam, through java.

My device is at /dev/video1, I basically just need the commands to disable autofocus, the java stuff I can do. I think it has something to do with v4l-utils but that's as far as I can get before my brain starts to explode.

Can anybody lend a hand?

Cheers

---

### Post by roelforg on 2012-02-24
IIRC: That's HW, can't disable.

---

### Post by boblettoj99 on 2012-02-24
I installed something called qv4l2 which seems to be a graphical interface for v4l-utils. I could disable it on there so surely there must be a command?!

---

### Post by roelforg on 2012-02-24
If it's possible, i don't know how.

Why would you anyway?

---

### Post by boblettoj99 on 2012-02-24
I need to disable it while I find intrinsic camera properties. I'm doing an image processing program, I think it'd be a bit much to ask users to disable autofocus themselves!

---

### Post by SoFl W on 2012-02-24
> **roelforg said:**
> If it's possible, i don't know how.
Why would you anyway?

Having worked professionally in video we used to have a saying, "auto xxx doesn't."  meaning the auto focus/white balance/(whatever) never did as good of a job as manual.  A lot has changed in that time and I have seen many improvements but sometimes auto focus doesn't focus on what you want it to focus on.

---

### Post by boblettoj99 on 2012-02-24
Well who made qv4l2? They must know!

---

### Post by boblettoj99 on 2012-02-24
I've found a handy little utility, lovingly called uvcdynctrl.

In command line..

```
uvcdynctrl -v -d video1 --set='Focus, Auto' 0
```

..works an absolute treat! It is confirmed by..

```
uvcdynctrl -v -d video1 --get='Focus, Auto'
```

..which returns 0, and then 1 if I change it back to 1. Also confirmed working in camorama (no auto focus).

However, when I try this in Java with...

```
try {
      		Process process = Runtime.getRuntime().exec("uvcdynctrl -v -d video1 --set='Focus, Auto' 0");
      		BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(process.getInputStream()));
      	    String line;
      	    while ((line = bufferedReader.readLine()) != null) {
      	        System.out.println(line);
      	    }
      	} catch (IOException e) {
      		e.printStackTrace();
      	}
```

..it just gives me "ERROR: Unknown control specified.".

I don't think I've done anything wrong with java, as running one of the uvcdynctrl options gives me the correct output. Could it be something to do with escape characters?

ARghhhh

---

### Post by boblettoj99 on 2012-02-25
Hooray, fixed it. For those that are interested:

In the end I had to write a simple bash script called autofocus.sh in the root directory of my java project, just the one line:

```
uvcdynctrl -d video$1 -s 'Focus, Auto' 0
```

And then from within java:

```
Runtime.getRuntime().exec("./autofocus.sh " + CAMERA_DEVICE_NUMBER);
```

Where CAMERA_DEVICE_NUMBER is the device number of your webcam. If you only have one this will be 0.

---

