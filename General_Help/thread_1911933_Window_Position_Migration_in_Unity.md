---
title: "Window Position Migration in Unity?"
date: 2012-01-19
forum: General Help
---

### Post by rmccarri on 2012-01-19
Hi everyone,
I've been struggling with what I thought was a Matlab issue all day.  I'm running Ubuntu 11.10 64 bit with Matlab R2011a and I've been running into an issue with a lag in the get command which turned out to be a window position issue.  In Matlab, you can specify a figure window position using figure and set and get the position of the window using the get command.  If I execute the following commands via a script window (i.e. selecting all and then evaluating the selection) it works fine:

```
>> clear all

figure('Position',[50,420,940,480])
get(gcf,'Position')

ans =

    50   420   940   480
```

However, if I introduce a pause of one second between the setting of the figure position and the probe, the figure apparently shifts and there's a lag in how long it takes to determine the position:

```
>> clear all

figure('Position',[50,420,940,480])
pause(1)
get(gcf,'Position')

ans =

    43   420   940   480
```

There doesn't appear to be an actual shift in the window position, just in how Ubuntu reports it.  Has anyone else run into a similar issue or know what might be cuaseing this?  Initially, I thought that it was a Matlab issue, but everything runs fine in Windows XP 32 bit and OpenSUSE 10.3 64 bit systems running the same version of Matlab.  It really does seem to be tied to Ubuntu.
Thanks for any suggestions or information.

---

### Post by rmccarri on 2012-01-20
Hi Everyone,
So I played around with this some more and it seems that it's the 3D effects that are causing the issue.  If I boot into 2D mode, everything works fine.  I just thought that I would post this workaround in case anyone else ran into the issue.

---

