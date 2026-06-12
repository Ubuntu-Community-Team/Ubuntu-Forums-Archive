---
title: "LCD-TV monitor resolution help (Basic)"
date: 2009-08-21
forum: General Help
---

### Post by mac666 on 2009-08-21
Hey
Thanks for a great forum... 

Im trying to tell my LCD-TV Monitor to use a resolution that aint in the Nvidia X Server resolution list for the monitor. I Think the resoultion i want is 1720x1080 or something (?). Its a 42" Full HD LCD 19/9 aspect...

If i use 1920x1080 the Desktop is outside the screen some how... (The TV doesnt have pixel mapping)
So when i watch a movie, some of the conent is outside the screen...

If its hard to change the "scale" of the screen i guess i will have to use another resolution.
In the list of avaible resolutions i have:
1920x1080
1420x360 (!!!!)
800x600
And some lower ones...

How could i add another resolution?
Is it hard to make a good scale down of the screen? (And that is automatic applied each time?)
Does anyone know which resulotion im looking for?
Thanks!

Im new at Linux so dont be to harsh!
Sorry for bad english

---

### Post by tgeer43 on 2009-08-21
Your English is better than the vast majority of native speakers. :wink:

On the Nvidia Xserver Display Configuration screen does it detect your display when you click the 'Detect Displays' button? If so, then try 'Auto' for the display resolution.

Also, click the 'Advanced' button and make sure that the panning is set to 1720x1080 or whatever resolution you end up using that fits the entire display inside your physical screen.

Hope this helps,

tgeer

---

### Post by Baasha on 2009-08-21
I am certainly no expert, but on my LCD tv there are options for increasing the image size.  These are intended to take a 4:3 image and blow it up to help fill the screen and make it look like a 16:9.  Have a look in your tv options.  If you have something similar maybe you could use this to reduce your image to regain what has gone  outside the screen area.  Just a thought.

---

### Post by tgalati4 on 2009-08-21
Most LCD TV's can only support 1280 x 1024 through the VGA port, regardless of what the actual screen resolution is.

---

### Post by mac666 on 2009-08-22
Thanks but i tried panning last night and the configurator swaps back to 1920x1080 the moment i release the focus from the input...

Im using a DVI and with Windows Vista, i get perfect with with the 1720x*** resolution...
I have to reboot each time i start the TV, very annoying!:(
I cannot use the auto resolution, it gives me 1920x1080... too high res!

My stupid TV doesnt have any good aspect settings....

BTW, If im not being clear please ask me. Sometimes my english fails me...:(

---

### Post by tgalati4 on 2009-08-22
This looks like a bug in the nVidia proprietary driver.  Try sending an email that describes your problem to nVidia.  I'd be curious to see their response.

---

### Post by mac666 on 2009-08-29
> **tgalati4 said:**
> This looks like a bug in the nVidia proprietary driver.  Try sending an email that describes your problem to nVidia.  I'd be curious to see their response.

yeah... i will do so... Sorry for the delay, have been away from home

---

