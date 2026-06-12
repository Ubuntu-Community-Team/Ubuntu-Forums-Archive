---
title: "Terminal install, update won't finish"
date: 2011-03-22
forum: General Help
---

### Post by ScroobeX on 2011-03-22
Hi guys, thanks for reading this.

I'm having an issue here. I'm trying to update program through the terminal, and I'm using the tarball unpacked to home directory. I do everything by the book, as explained in the "readme" file inside the tarball. I'm using Seamonkey 2.0.11 (or so it says) and I want to update it to 2.1 beta2. Anyway, when I'm in the terminal and in the directory I type "./seamonkey" and there it goes, new version is installed, functioning, and you can browse it all day long. That is, until you close one of the two, either terminal or the updated Seamonkey. After closing and starting seamonkey again, it's reinstalling the old 2.0.11 version. If you want to close the terminal first, the terminal says 'one of the programs is open within terminal, closing the terminal will kill the program'. Then both would close, and again when you start it, it's rolled back to previous version. 

Now, would anyone there know a trick how to finish the update all the way, so I don't have to do it over and over again?

Here is the error message I get in the terminal after closing v2.1b:
> (seamonkey-bin:6949): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(seamonkey-bin:6949): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed[COLOR=Navy]Thanks a lot![/COLOR]

---

### Post by jerome1232 on 2011-03-22
You did the part where you added a new launcher for seamonkey correct?


That's just the entire program in that tar archive, all you have to do is create a new launcher on your panel and point it to that seamonkey executable, where ever you put it.

---

### Post by ScroobeX on 2011-03-22
> **jerome1232 said:**
> You did the part where you added a new launcher for seamonkey correct?


That's just the entire program in that tar archive, all you have to do is create a new launcher on your panel and point it to that seamonkey executable, where ever you put it.
You mean I need to make a shortcut first to do that update? Or just to use the program?

I did that, again it's updated. But close it, and open it again from "proper" menu it goes back to the old version. A vicious circle.
Start program from menu shortcut while updated version is open, opens the new beta version. Close all windows and start from usual menu shortcut, installs an old version.

Does it have to be like that? Is it normal to have two seamonkeys and two firefoxes if you want to use the beta version? Why is impossible to finish the update in the terminal? The error message in the terminal says this
> NOTE: child process received `Goodbye', closing down

(seamonkey-bin:4800): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(seamonkey-bin:4800): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed
Don't think I'm a sort of expert with the terminal, I'm not :)

Cheers

---

### Post by jerome1232 on 2011-03-22
Okay, basically you haven't updated anything, you downloaded a beta version. The beta version is what you extracted from that archive.

You still have your regular version that you access by click on the icon in your menu, currently the only way for you to launch the beta version you downloaded is to either double click it's executable (seamonkey) that you extracted or to run it from a terminal by cd'ing into it's directory and using ./seamonkey. That executable is NOT an installer, it's actually the new version of seamonkey.

So when you type ./seamonkey your actually running the beta version, not updating your current version to the beta.


Are you following what I'm saying?

If you wanted an easy to click launcher in your menu you can probably right click on your panel and add a launcher that executes the executable you downloaded.

Let me know if I'm being clear as mud! I'm trying best as I can to explain it. :D

If you wanted to replace your current version of seamonkey with this beta version, an easyway would be to remove the seamonkey you have installed, create a launcher script and put a symnlink to the launcher script in /usr/bin/local. Let me know if that is something your interested in.

---

### Post by ScroobeX on 2011-03-22
> If you wanted an easy to click launcher in your menu you can probably  right click on your panel and add a launcher that executes the  executable you downloaded.

Let me know if I'm being clear as mud! _I'm trying best as I can to explain it._ :DDon't worry, I took note of that :D

Well we already did put a launcher on the top panel did we not? And it works perfectly.

So basically what you're saying is that the beta programs in Ubuntu, or perhaps just this one, are not meant to be installed and replace the current version of software, until the new version comes out, if I understand you properly. 

> If you wanted to replace your current version of seamonkey with this  beta version, an easyway would be to remove the seamonkey you have  installed, create a launcher script and put a symnlink to the launcher  script in /usr/bin/local. Let me know if that is something your  interested in.Does putting a symnlink (whatever that is) in /usr/bin/local mean placing the launcher inside the main menu? Is that something similar to right click on desktop and clicking "create launcher" or it's a different thing altogether?

What I'm trying here is to figure out how to run or install programs in Ubuntu, it's frustrating to know there's a program somewhere and you can't even run it. I got no knowledge of programming or compiling code so if scripting the launcher involves some heavy-duty code this might be a waste of your precious time :P

---

### Post by jerome1232 on 2011-03-22
You can think of a symnlink as something equivalent to a Shortcut in Windows.


So first are you happy with it being just installed for your user or do you want a system wide install?


If your happy with it being for your user then I would just add a shortcut to your panel of menu and be done with it. Screenshot examples of me doing that below.

Basically your right click your menu, click edit menu's, click add new item. You can find a nice seamonkey icon inside the archive.

If you want a systemwide install then we just have to copy the whole thing to someplace (after looking at it we don't need a launcher script, they arleady made one) like /usr/local and make a symlink in /usr/local/bin

So say it was in your Downloads folder

```
sudo mv ~/Downloads/seamonkey /usr/local
sudo ln -s /usr/local/seamonkey/seamonkey /usr/local/bin/seamonkey-beta
sudo chown -r root:root /usr/local/seamonkey
sudo chmod +x /usr/local/bin/seamonkey-beta
```

Then create your launchers as above but just use seamonkey-beta as the command, get your icon from /usr/local/seamonkey/icons.

Hope that helps.

---

### Post by ScroobeX on 2011-03-23
I took a screenshot of that code, it seems to be potentially useful for the future installations, and perhaps one can also in time figure out what directory plays which role in Ubuntu file system. So let me see if I got this right, with my Linux "knowledge":

First you move the downloaded directory to a directory similar to "program files" in windows, then you create a link in the executive directory putting the appropriate "anchor", then you change the owner to "everyone", and then you make the symnlink executable in the last line, so you can run as any other installed program, is that so.

Well, this kind of support one can never get when calling those 'technical support' lines by the big companies, they must be envious and with furious red face if they are reading this. If all the help was this focused Linux would spread fast as lightening.

Thanks for doing the screenshots up there as well!

---

### Post by jerome1232 on 2011-03-23
> **ScroobeX said:**
> 
First you move the downloaded directory to a directory similar to "program files" in windows, then you create a link in the executive directory putting the appropriate "anchor", [COLOR="Red"]then you change the owner to "everyone"[/COLOR]

Correct on all points except the red one, we actually changed the ownership to root, meaning only users with administrator rights can modify the files, not just any user.

Any user configured settings are stored in your home directory.

That way malicious script number 54673 can't theoretically modify the executable's and make seamonkey do bad things.


/usr/local is one a few places that are typically used to install manually installed programs. /opt is another.

---

### Post by ScroobeX on 2011-03-23
Alright, so changing the owner to root means only administrators can make the changes.

It's good to know it's on the safe side as well.

Thanks again Jerome!

---

