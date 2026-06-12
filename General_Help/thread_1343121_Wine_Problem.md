---
title: "Wine Problem"
date: 2009-12-01
forum: General Help
---

### Post by Joshooarh on 2009-12-01
I have a problem with wine.
A few days ago I was messing round with the screen settings and made it start in a window. I changed various other things but I have no idea what. After restarting my computer however, I have nothing on the screen when I start wine. I have tried multiple applications (inc. Configure Wine) but I have the same result every time, a blue screen in a window. There is not a window in the window as there used to be, it is completly blank.

Ideas on how to fix this, anyone?

P.S: I am using Easy Peasy which is basically Ubuntu Netbook Remix relabelled ( I have all the netbook stuff turned off though so its practically ubuntu).

---

### Post by realbiga on 2009-12-06
Since your post is a *bit* vague on what settings you were changing the only solution i can offer would be to completely remove & purge wine and reinstall it. 
im very uncomfortable purging/removing files before seeing exactly what apt is going to do so i normally run the command simulated first so i can be sure it wont have unintended consequences.
```
sudo apt-get purge -s wine
```
to purge (remove wine & its config files)
```
sudo apt-get purge wine
```
after purging wine check that your .wine folder in your home directory is gone 
```
cd ~
```
```
ls -a | grep wine
```
if the .wine directory is still there then remove it 
```
rm -r .wine
```
now you just have to reinstall wine (and whatever programs you had installed in wine
1st update your package list
```
sudo apt-get update
```
then install wine 
```
sudo apt-get install wine
```

just a little hint for the future. If you want to play with the settings in wine after you start the "configure wine" program under the "APPLICATIONS" tab you can add one of your windows programs allowing you to adjust settings in the "graphics" and "libraries" tabs without fear of screwing up the default behavior. Although if you change more than 1 setting at a time it is difficult to ascribe a new behavior, positive or negative, to the appropriate action. This lack of a definite causal relationship makes it difficult to replicate (or in your case reverse) the changes... ie only change one setting at a time:). If something gets weird just delete that profile and all will be as it was. 
Last little suggestion
vague posts arent very useful to DX a problem. Im not even sure where you were when you refer to "screen settings," wine? gnome? metacity? compiz? none of which actually have a "screen settings" option. Also information such as what version of the offending program you are running tends to be helpful.
No worries though, I cant tell you how many programs & entire distros i have had to re-install b/c of my messing around:)

---

