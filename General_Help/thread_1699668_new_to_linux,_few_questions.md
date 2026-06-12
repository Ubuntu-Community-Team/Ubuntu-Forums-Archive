---
title: "new to linux, few questions"
date: 2011-03-04
forum: General Help
---

### Post by soraxd on 2011-03-04
hello everyone, so ive been using ubuntu for a few days now, im used to windows. i have a few questions hopefully someone can answer.

1, when i select files on my flashdrive and press delete, they dissapear, but theyre still there invisably, i know this because my 16gb flashdrive only have 1gb of memory left, after ive deleted everything off it. then when i plug it into windows it shows up and it says theres a folder called trash, where everything is.. so whats up with this? why is ubuntu doing this when i try to delete?

2, drivers to make connected things show. for example my phone needs to have drivers installed to appear on my windows (Galaxy S), another thing would be an external hard drive, i want to buy one, but worry that since external hard drivers need to install drivers to be read, i wont be able to use one.. is there a solution for this?

3, whats better for linux, google chrome or chromium web browser?

thats all i can think of for right now, thanks!

---

### Post by colmeweb on 2011-03-04
Welcome to the community.

1. When you delete something on your flash drive it is moved to trash, you have to empty your trash before it is permanently deleted. I could be wrong about that, but it seems to be what happens with me.

2. I don't know what drivers you would need exactly, but I use a 1TB external and it worked on day one with Ubuntu. I don't think you will have any problems with an external drive

3. If you go to the Ubuntu Software Center there is a packet for chromium that you can download. I have been using it for a few months and it works fine, except that it is a little twitchy with flash.

Good luck with everything.

---

### Post by jocko on 2011-03-04
> **soraxd said:**
> hello everyone, so ive been using ubuntu for a few days now, im used to windows. i have a few questions hopefully someone can answer.

1, when i select files on my flashdrive and press delete, they dissapear, but theyre still there invisably, i know this because my 16gb flashdrive only have 1gb of memory left, after ive deleted everything off it. then when i plug it into windows it shows up and it says theres a folder called trash, where everything is.. so whats up with this? why is ubuntu doing this when i try to delete?
Linux does exactly what windows does. If you only press delete, it moves things to trash. Just empty your trash. Or press Shift+delete do delete immediately without sending anything to trash. Exactly like in windows...

> **soraxd said:**
> 2, drivers to make connected things show. for example my phone needs to have drivers installed to appear on my windows (Galaxy S), another thing would be an external hard drive, i want to buy one, but worry that since external hard drivers need to install drivers to be read, i wont be able to use one.. is there a solution for this?
You really need drivers to connect your phone in windows? If that's true, Samsung is just being silly.
And why would you need drivers for an external hard drive? I've never seen an external drive that need a driver. True, windows by some reason pretends to install something every time you plug in a new usb device, but that behaviour is specific to windows... 

> **soraxd said:**
> 3, whats better for linux, google chrome or chromium web browser?

thats all i can think of for right now, thanks!
That's your personal choice. Isn't the main difference between google chrome and chromium the google branding and some license issues?

---

### Post by polardude1983 on 2011-03-04
Yeah basically the only difference between Chromium and chrome. Is Chromium is chrome but without the EULA.

But chromium was twitchy with flash for me. So i installed chrome.

---

### Post by soraxd on 2011-03-04
thanks so much guys, linux is really different from windows, so its hard to adapt, but im liking it more and more as i understand it better!

---

### Post by dudesks on 2011-03-04
To help others please mark solved threads as 'Solved' from 'Thread Tools' at top right

---

### Post by dionysius on 2011-03-04
> **soraxd said:**
> hello everyone, so ive been using ubuntu for a few days now, im used to windows. i have a few questions hopefully someone can answer.

1, when i select files on my flashdrive and press delete, they dissapear, but theyre still there invisably, i know this because my 16gb flashdrive only have 1gb of memory left, after ive deleted everything off it. then when i plug it into windows it shows up and it says theres a folder called trash, where everything is.. so whats up with this? why is ubuntu doing this when i try to delete?

2, drivers to make connected things show. for example my phone needs to have drivers installed to appear on my windows (Galaxy S), another thing would be an external hard drive, i want to buy one, but worry that since external hard drivers need to install drivers to be read, i wont be able to use one.. is there a solution for this?

3, whats better for linux, google chrome or chromium web browser?

thats all i can think of for right now, thanks!


1. In addition to what others have said, Ubuntu creates a hidden trash folder, preceded with a '.' ( a dot in front of a file or folder name hides it). This gives you the chance to save something you've deleted by accident. A good thing, in my opinion. You could use the shift+del option as jocko has said, or press ctrl+h and the hidden '.Trash-100' folder shows up, which can then be permanently deleted. Alternatively, you could edit the settings in Nautilus (file browser) to always show hidden files and folders. 

2. None of the peripherals you use should need additional drivers. Mice, keyboards, external storage, basically anything that plugs in using USB is automagically recognised and ready to use. The only thing you may have trouble with is Windows specific software for your external devices: some have 'control panel' software or other 'features' for which you'll need to run Windows executables. From what I read you should be able to use your Galaxy S as a mass storage device attached to Ubuntu: just select the 'mass storage' option on your phone's screen when you attach it to your laptop/computer. External hard drives should work without additional drivers, and will show up under /media If something doesn't work, search the forums and if there's no solution post a thread and people will be happy to help. 

3. I'd use the chromium package in the Ubuntu repositories (software centre, synaptic or apt-get) rather than downloading from the interweb. Chromium is updated regularly, and is thoroughly checked before updates are released by the package maintainers. Saves you having to check for updates, and keeps both your browser and system working as they should. 


Try to forget most of what you know how things work on Windows - what you think of as 'normal' in terms of how things are/should be is nothing more but how Windows handles things. Ubuntu, and Linux distros in general, has a different approach. Good luck and please ask when you come across something 'odd' or need help with something.

---

### Post by mastablasta on 2011-03-04
> **jocko said:**
> Linux does exactly what windows does. If you only press delete, it moves things to trash. Just empty your trash. Or press Shift+delete do delete immediately without sending anything to trash. Exactly like in windows...

 
It's not exactly like windows - windows marks the space on disk as avaialbale for writing and is alter overwritten. in linux it just moves the files and that space still occupies the disk. until you delete the files from it. so no, not the same at all.
 
 
> 
And why would you need drivers for an external hard drive? I've never seen an external drive that need a driver. True, windows by some reason pretends to install something every time you plug in a new usb device, but that behaviour is specific to windows... 
 
 
perhaps you never saw drivers, because they are "installed" when you boot in linux . remember linux has drivers as part of the kernel. any device plugged to motherboards needs drivers in order to run. 
 
external drives often need drivers that propperly power them down, enable power saving etc. on them. so if manufacutrer provides them then they are probably better than the ones in windows. sometimes devices are also non standard, so standard driver don't work.

---

### Post by jerome1232 on 2011-03-04
> **mastablasta said:**
> It's not exactly like windows - windows marks the space on disk as avaialbale for writing and is alter overwritten. in linux it just moves the files and that space still occupies the disk. until you delete the files from it. so no, not the same at all.
 

Windows uses trash just like Ubuntu does.

Just not on external media, like Ubuntu does.

---

### Post by marl30 on 2011-03-04
> **dapwalvekar said:**
> I am new for linux.I did'nt used this os.So for using this give some steps.

Hi, welcome to the forum. :)

 It would be better if you could start a thread in this section to ask the question you're asking, since this thread is related to some other questions being asked by another new member.

---

