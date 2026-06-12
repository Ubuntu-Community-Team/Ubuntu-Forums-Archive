---
title: "Everything is maximised/ too big"
date: 2011-09-22
forum: General Help
---

### Post by UncleMonty on 2011-09-22
I just booted up my desktop now and everything has gone really big. The folders, the apps, the writing everything (but the font size is set to 10). The folders don't all fit on the screen. Can anything explain how I can get rid of this please?

(I am using Ubuntu 10.04 LTS).

---

### Post by patryk77 on 2011-09-22
Could your resolution have changed?

Open the terminal and post the output of:
 xrandr

---

### Post by UncleMonty on 2011-09-22
> **patryk77 said:**
> Could your resolution have changed?

Open the terminal and post the output of:
 xrandr


Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0

---

### Post by patryk77 on 2011-09-22
Is that your screen's maximum resolution?

Could be related to the DPI, under System/Preferences / Appearance / Fonts / Details, Resolution should be set to 96 dots per inch.

Though if your screen supports resolutions higher than 1024x768, then that would be the culprit.

---

### Post by UncleMonty on 2011-09-22
> **patryk77 said:**
> Is that your screen's maximum resolution?

Could be related to the DPI, under System/Preferences / Appearance / Fonts / Details, Resolution should be set to 96 dots per inch.

Though if your screen supports resolutions higher than 1024x768, then that would be the culprit.


Yep it's set to 96 dots per inch.
Have no idea what the highest screen resolution is.

---

### Post by patryk77 on 2011-09-22
What's the screen's model?

---

### Post by UncleMonty on 2011-09-22
> **patryk77 said:**
> What's the screen's model?

According to: 

[http://www.whatismyscreenresolution.com/](http://www.whatismyscreenresolution.com/)

I have 1024 x 768

---

### Post by patryk77 on 2011-09-23
> YOU ARE USING
1366 x 768


```
$ xrandr 
Screen 0: minimum 3286 x 1080, current 3286 x 1080, maximum 3286 x 1080
default connected 3286x1080+0+0 0mm x 0mm
   3286x1080      50.0* 

```

I have my lappy on one screen with a 1080p TV on another.

The site doesn't give an accurate reading.

Are you using a standalone screen, or is it on a laptop?

Either way, what Make (Toshiba, Sorny, Viewsonic) and Model is it?

---

### Post by UncleMonty on 2011-09-23
It's a standard alone screen. 

The make is Octigen. 

Model - MA7CKA


> **patryk77 said:**
> ```
$ xrandr 
Screen 0: minimum 3286 x 1080, current 3286 x 1080, maximum 3286 x 1080
default connected 3286x1080+0+0 0mm x 0mm
   3286x1080      50.0* 

```

I have my lappy on one screen with a 1080p TV on another.

The site doesn't give an accurate reading.

Are you using a standalone screen, or is it on a laptop?

Either way, what Make (Toshiba, Sorny, Viewsonic) and Model is it?

---

