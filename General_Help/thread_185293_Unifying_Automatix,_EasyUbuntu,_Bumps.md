---
title: "Unifying Automatix, EasyUbuntu, Bumps"
date: 2006-05-31
forum: General Help
---

### Post by ago on 2006-05-31
I think that, like me, many here desire to see the 3 apps unified into one. I know that there are difficulties, technical ones and personal ones... I know that there are different views, different goals etc, etc... And I know far too well the story about "how choices are good"... But the current situation is confusing particularly considering the target audience...

We are talking about packages to simplify user experience, particularly new users... Many of them probably are just recovering from the news that there is no such thing as "one linux"... Then they find out that there is no such thing as "one desktop"... And when they finally make their choice and turn to a simple distro, they discover that they need external packages to simplify the simple distro...  I think that adding the final blow of throwing at them several "simplifying packages" is a bit too much... Not to mention the duplication of work...

I am not intimately familiar with any of the packages but I guess some common ground can be found, considering that the underlying scripts should probably be very-very similar anyway... And also because the above packages are subtly different and somewhat complementary. The relation between EasyUbuntu and AutoMatix is IMO similar to the one between AddRemoveProgram  and Synaptic. Both can coexist as different front-ends to the same scripts: simplified and advanced. And Bumps can be regarded as a specific "plugin" for multimedia codecs... 

Following are some random thoughts on the topic:[LIST=1]
[*]The 3 apps could be unified rewriting them in a common language (probably **python** would be a good choice)
[*]**Plugin structure** to add new actions (which might be added using normal .deb packages).
[*]EasyUbuntu could be used as a default "**simplified front-end**"
[*]Automatix could be used as an "**advanced front-end**"
[*]Bumps could be the plugin focusing on the **multimedia codecs**
[*]The inteface should have a panel with the usual scrolllist with checkboxes to select the actions, and a second (tabbed) panel that shows **info on the selected item**: description, legal status, installation gotchas, what files are affected (ad in particular packages installed+dependencies and which existing file is going to be modified), **how to do the same thing manually**
[*]The same info should be added to a common **wiki**, which would also be useful as a base for a new version of the ubuntuguide
[*]When you proceed you get a **confirmation box** with a summary: packages selected, the legal status required for the selected packages, files affected, postinstall manual tasks required.[/LIST]

---

### Post by ago on 2006-05-31
I found this interesting thread: 
[http://www.ubuntuforums.org/showthread.php?t=177858](http://www.ubuntuforums.org/showthread.php?t=177858)

---

### Post by Kevin on 2006-05-31
All three projects have people working on them, and they all do their tasks quite well.

I agree though that it is confusing for a new user, trying to set up his new Ubuntu installation, to choose which one to use.  Someone who is new to everything, could end up with a whole bunch of stuff they never use if they used Automatix for example.

This is why I think we need one sticky, in the same vein as the one about Xgl and such, that explains all three and the differences between them.  Such a sticky could be titled "How to get your new Ubuntu installation ready for you" or something like that.  Then it would start with the simplest program, likely BUMPS since it installs nothing but codecs and flash and stuff, then maybe explain EasyUbuntu for people who want more, and then explain how to get Automatix for those who want something more advanced.

This way we get less questions about which one to use, and less people getting confused by lots of new programs, or lots of options, and the such.

Just my 2 cents

---

### Post by elamericano on 2006-05-31
What your well-intentioned post describes is the subject of paralell projects. The problem is the same as "forking", where variations of the same project continue to be maintained just because they have enough manpower to do it. They can be in the extreme minority, but they don't have to die just because the reasonable majority prefers something else. This fragmentation is commonly cited as one of the major weaknesses of open source. Linux is about choice, but sometimes it goes too far.

In short, you can forget about unification. Your best hope is that one "wins" by offering everything the others do and more, thus becoming the unofficial recommendation of all forums.

Automatix was my choice last time based on functionality, but EasyUbuntu has the project structure to be the trusted app for this purpose. Time will tell.

---

### Post by aysiu on 2006-05-31
[QUOTE=Kevin]
This is why I think we need one sticky, in the same vein as the one about Xgl and such, that explains all three and the differences between them.  Such a sticky could be titled "How to get your new Ubuntu installation ready for you" or something like that.  Then it would start with the simplest program, likely BUMPS since it installs nothing but codecs and flash and stuff, then maybe explain EasyUbuntu for people who want more, and then explain how to get Automatix for those who want something more advanced.

Just my 2 cents[/QUOTE] I happen to agree with your two cents.

Let's make that four cents.

---

### Post by Kevin on 2006-06-01
Well, I wrote a quick one up, any suggestions?  If it's good, then I'll start a new thread with it and hopefully someone will sticky it!

_________

So you've finally got your new Ubuntu 6.06 installation working, and now you need to get it ready for daily use.  Depending on how you use your computer, there might still be some things for you to do.

One of the most often asked questions, is how to get Ubuntu multimedia ready.  This includes things like audio and video codecs, DVD playback, as well as internet content such as Flash.  For a basic program that gets these things set up for you, but changes nothing else in your brand new Ubuntu installation, there is:

[SIZE="4"]**Method #1 - BUMPS - Basic Ubuntu Multimedia Preparation Script**[/SIZE]

Step 1:  More information about BUMPS including the packages it installs is available [here.]("http://http://www.ubuntuforums.org/showthread.php?t=181248")

Step 2:  BUMPS can be downloaded from [this thread.]("http://www.ubuntuforums.org/showthread.php?t=181251")

Step 3:  Simply double click the script and select run, or run it from the command line, and follow the instructions!

[SIZE="4"]**Method #2 - EasyUbuntu**[/SIZE]

EasyUbuntu installs a few more things than BUMPS, including 3d Acceleration for nVidia and ATI users, as well as some file sharing applications, and will also get your multimedia set up.

Step 1:  More information about EasyUbuntu can be found [here.]("http://easyubuntu.freecontrib.org/")

Step 2:  EasyUbuntu can now be downloaded from [this page.]("http://easyubuntu.freecontrib.org/get.html")  Instructions on how to download and run it are all there.

[SIZE="4"]**Method #3 - Automatix**[/SIZE]

Some users may want to install lots of additional software, and have many additional things set up for them.  For this there is Automatix.

Step 1:  More information on Automatix, as well as a download link, can be found in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=177646")

Step 2:  Double click the file downloaded, and install the package.

Step 3:  There should now be a menu link for Automatix, and you can use it to install the additional software.

**General Note!**

If you'd like to learn about what these programs are doing, or how to do it yourself, a great page to start is the wiki entry on RestrictedFormats.

This page can be found [here.]("https://wiki.ubuntu.com/RestrictedFormats")

That's all for now, I'll try and keep this thread updated as things change.

---

### Post by syxbit on 2006-06-01
elamericano couldn't be more right.
choice is good, but too much choice is very bad. it can lead to lots of bad options...
just imagine if the guys behind kde and gnome had joined and just written 1 desktop
i know there'd be pro's and con's, and competition is good etc... but just think about it.
kevin's explination is great too!
i first installed ubuntu 8 months ago, and was shocked that it wouldn't play even mp3's!
if ubuntu is really going to be "for human beings" it needs to make adding that functionality REALLY EASY.
i'm fed up with those stupid linux guru's who actually want things to be complicated, with tons of stuff in the terminal.
99% of regular computer users prefer to do stuff in the gui.
joining all 3 would be great, but highly unlikely, as they'd have to compromise.

btw...have you guys read about the new ideas for edgy eft ?
one of the things they're going to try to do is "make easyubuntu and automatic obsolete"
check [here]("https://wiki.ubuntu.com/EdgyIdeas")

---

### Post by philipacamaniac on 2006-06-01
[quote=syxbit]btw...have you guys read about the new ideas for edgy eft ?
one of the things they're going to try to do is "make easyubuntu and automatic obsolete"
check [here]("https://wiki.ubuntu.com/EdgyIdeas")[/quote] 
I think a more appropriate explanation of that wikilink is due, so here goes. That page, EdgyIdeas, is simply a braindump of just one of the Ubuntu developers (although it has had 2 edits by other wiki users). There are many Ubuntu developers and community contributors who will ultimately decide the fate of Edgy Eft. No one should refer to that page as an official feature plan.

I don't think it will ever be possible to "make EasyUbuntu and Automatix obsolete" because[LIST]
[*]Ubuntu would be heavily criticized by the FSF and Debian communities for including proprietary (non-free) software[/LIST][LIST]
[*]They would not likely include any proprietary software on the CD, even if the Multiverse and Restricted components were enabled by default. So a script would most certainly be written somewhere to download the necessary packages automatically; it would just be easier this time.[/LIST][LIST]
[*]PLF will always exist due to patents in the US, so BUMPS and other multimedia codec scripts will always be around for the newbies.[/LIST]Just my humble opinion!

---

### Post by adam.tropics on 2006-06-01
I have not used EasyUbuntu, and so am not wholly qualified to comment. However, as I see it so far, Automatix has primarily been around to support the current stable release, and to his well deserved credit, Arnieboy has provided a huge amount of support in its regard. He has also unfortunaltely from time to time been victim of some pretty ridiculous and nasty posts for his effort. Hopefully that is all now in the past! Anyway, on the flipside, Bumps has mainly been involved with the development release, and again its author has provided much support and so on with that. Given the authors are apparently then interested in differing areas of Ubuntu, stable and development, then perhaps they should focus their efforts accordingly. 

I just don't see this as a competition, and whilst I can see where the confusion for new users could come from, perhaps the answer is for Bumps to be the development tool, and become obsolete as the version is released, and Automatix to then take the reigns of the stable release. Just an idea!

---

### Post by ago on 2006-06-01
My take on this is simple... Automatix has to be rewritten anyway according to thread "Automatix2".

They will probably use python. Which I think is a good choice.
It will probably be "modular". Which is a good choice.

If now you have an "engine" that provides common functionality (logging, backup...), uses plug-ins to import the list of available actions, and can use different front-ends... That could easily be used as a base to incorporate the other projects. 

Bumps could simply write plugins for multimedia. EasyUbuntu could be incorporated as meta-plugins to accomplish broad tasks + simplified front-end... 

In fact being python/plugin based it could be a general program not strictly related to Ubuntu.

---

### Post by ago on 2006-06-01
And by the way, EasyUbuntu is already written in python...

So at least on Python the agreement should be easy...

All is needed is to create a plug-in engine independent of the front-end (which is fairly easy in python: each plugin is a module with a set of standard attributes dropped in a specific folder. The plugin being dynamically imporyed)... And the different groups can simply add their own scripts/front-ends to accomodate their own goals/preferences.

I think that unifying the 3 projects is going to be less difficult than people imagine...

---

### Post by ago on 2006-06-01
[QUOTE=Kevin]Well, I wrote a quick one up, any suggestions?  If it's good, then I'll start a new thread with it and hopefully someone will sticky it![/QUOTE]

Excellent guide, Thanks :-D

---

### Post by ago on 2006-06-01
An extremely simplified (and untested) schema for a python based plug-in/engine could be

```

'''plugins/samplePlugin.py'''
uid = u"{1234...}"
name = "samplePlugin"
version = "v0.1"
category = "multimedia"
shortDescription = "This plugin does xyz"
longDescription = "Bla bla bla"
manualEquivalent = "To do the same thing manually..."
legalStatus = "The programs are not included in official ubuntu because..."
legalWarning = "If you are a resident in country XYZ it is illegal..."
modifiedFiles = ["/etc/XYZ"]
requiredPlugins = [(uid1, version1), (uid2, version2)...]
requiredPackages = [("xyz", version1)]
requiredRepositories = ["abc"]
def install():
    pass
def isInstelled():
    pass
def uninstall():
    pass

```

```

'''plugins/__init__.py'''
__all__ = ["samplePlugin"]

```

The engine will do something like

```

'''engine.py'''
import plugins 
from plugins import *
class Engine:
	def __init__(self):
		self.loadPlugins()
	def loadPlugins(self):
		self.plugins = {}
		for pluginName in plugins.__all__:
			plugin = getattr(plugins, pluginName)
			self.plugins[plugin.uid] = plugin
	def install(self, selectedPlugins):
	    if not self.confirm(selectedPlugins): return
	    for plugin in selectedPlugins:
	        if plugin.isInstelled(): continue
			for rp in plugin.requiredPlugin:
	            requiredPlugin = self.plugins[rp[0]]
				requiredVersion = rp[1]
				if requiredPlugin.version < requiredVersion: 
					raise Exception()
				self.install([requiredPlugin])
	        for f in plugin.modifiedFiles:
	            self.backup(f)
	        self.installPackages(plugin.requiredRepositories, plugin.requiredPackages)
	        plugin.install()

```

---

### Post by ago on 2006-06-01
Another promising approach, to avoid reinventing the wheel, would be to package each action/plugin/script as a .deb package... Then you could simply reuse traditional apt tools... The packages could be added to the PLF repository...

Is a separate interface to run scripts really necessary? Deb packages can run scripts...

---

### Post by bluenova on 2006-06-01
Don't forget there are plans to get rid of all of them:
[Make automatix/EasyUbuntu/etc. obsolete](https://wiki.ubuntu.com/EdgyIdeas)

---

### Post by ago on 2006-06-01
Well the more I think on it the more I am convinced that the simplest and easiest way to unify the 3 applications would be to wrap th low-level scripts as deb packages... Possibly within the same categary and all hosted with relevant dependencies on the same repository (PLF).

Bumps for instance could be made into a deb package and hosted in PLF... Same thing for most of the "actions" in easyUbuntu/Automatix.

This approach would also be consistent withe the proposal: [https://wiki.ubuntu.com/EdgyIdeas](https://wiki.ubuntu.com/EdgyIdeas) since .deb packages would be needed anyway...

In fact if you wanted to unite the 3 apps you would need a plug-in framework and some code similar to the above... But if you look at the code you will soon notice that it is in fact replicating what apt already does very well... 

So there might in fact be a simple solution to the problem... I cannot see many shortcomings...

---

### Post by SeanTater on 2006-06-01
I vote edgy! Having it notify you to install xyz sounds much better than easyubuntu, etc!

---

### Post by eqisow on 2006-06-01
From [https://wiki.ubuntu.com/EdgyIdeas](https://wiki.ubuntu.com/EdgyIdeas):
> Make automatix/EasyUbuntu/etc. obsolete

    *Enable universe,multiverse by default
    *Suggest packages to support unknown file types
    *Extend Firefox plugin locator to find official packages of plugins
This is awesome and I fully support it, but what do you guys think about just having a single prompt on first boot that ask you if you want to install all multimedia packages and etc?

---

### Post by FrancoNero on 2006-06-01
[QUOTE=ago]
We are talking about packages to simplify user experience, particularly new users... Many of them probably are just recovering from the news that there is no such thing as "one linux"... Then they find out that there is no such thing as "one desktop"... And when they finally make their choice and turn to a simple distro, they discover that they need external packages to simplify the simple distro...  I think that adding the final blow of throwing at them several "simplifying packages" is a bit too much... Not to mention the duplication of work...[/QUOTE]

yeah after all it's Linux for Human Beings right, so we're not talking the advanced user we're talking EVERY user.
you can't expect from a "n00b" - as much as I hate to use that expression - to choose between different external tools to install things he isn't really sure why those aren't included in the first place, let alone those users who search synaptic in vain only to be told 4 months later after they switched back to Windows that you need to download lots of stuff to actually make Linux work for you as a multimedia OS (mp3s, dvds and stuff)

so yeah, not only am I for having one tool doing that I am also for having that as a shortcut on the standard ubuntu install desktop first thing the user sees is a step by step thing to put the final touches on his new OS

---

### Post by ago on 2006-06-01
I must say that I also fully understand the philosophy of ubuntu. And I agree that the use of closed/proprietary/restricted codecs/drivers should be disincentivized.

As far as I am concerned I try to avoid using such software and I orient my purchases to foster open standards whenever possible (e.g. ogg compliant mp3player). But sometimes it is necessary to use closed codecs (shall I throw away all my dvds?). 

So my view is that those items should not be in by default, but when someone tries to access a file that requires a particular codec instead of a cryptic error message he should receive a good explanation of the situation, what codec is needed, why is not available, legal status required... After this explanation he should be able, if he wants, to install the required programs EASILY. I am totally in favour of the proposal in Edgy...

Wrapping the scripts of easyubuntu/automatix/bumps into deb packages could simplify the above process. Creating a deb package for a simple tweaks might be overstretched (possibly simple tweeaks should be placed separately somewhere in the settings), but for anything else that requires installation of software, using deb packages is a good approach. Once in apt there are plenty of tools that can be used. Metapackages are obviously also a possibility, so that multiple actions could be performed in one go...

---

### Post by FrancoNero on 2006-06-01
[QUOTE=ago]
So my view is that those items should not be in by default, but when someone tries to access a file that requires a particular codec instead of a cryptic error message he should receive a good explanation of the situation, what codec is needed, why is not available, legal status required... After this explanation he should be able, if he wants, to install the required programs EASILY. I am totally in favour of the proposal in Edgy...[/QUOTE]

excellent proposal. i hope someone reads this ;-)

---

### Post by WildTangent on 2006-06-01
I cannot speak directly for the developers of Automatix on their opinion of merging, because I simply do not know, I am merely the developer for the website. However, I can say that they have already begun work on a python version, and yes, it will have plugin support as far as I know, as well as several other improvements. 

Our aim is first and foremost to create good, stable code that will work reliably. Our second aim is to give the most comprehensive selection of extra apps we can, whilst not bloating the app. Hence, we will have plugins for other types of apps that might not be the choice for the majority.

The point I am trying to make is that we are departing the current "norm" as it were with other apps similar to our own. Other apps are welcome to join us, or keep doing what they're doing. As a sidenote, I believe that the developer of BUMPS was approached for a possible merger, but he said that he would prefer to keep developing a script strictly geared towards multimedia capabilities, and respectably declined our offer.

WildTangent,
Automatix Website Team Lead

---

### Post by robotgeek on 2006-06-01
[QUOTE=ago]An extremely simplified (and untested) schema for a python based plug-in/engine could be

```

'''plugins/samplePlugin.py'''
uid = u"{1234...}"
name = "samplePlugin"
version = "v0.1"
category = "multimedia"
shortDescription = "This plugin does xyz"
longDescription = "Bla bla bla"
manualEquivalent = "To do the same thing manually..."
legalStatus = "The programs are not included in official ubuntu because..."
legalWarning = "If you are a resident in country XYZ it is illegal..."
modifiedFiles = ["/etc/XYZ"]
requiredPlugins = [(uid1, version1), (uid2, version2)...]
requiredPackages = [("xyz", version1)]
requiredRepositories = ["abc"]
def install():
    pass
def isInstelled():
    pass
def uninstall():
    pass

```

```

'''plugins/__init__.py'''
__all__ = ["samplePlugin"]

```

The engine will do something like

```

'''engine.py'''
import plugins 
from plugins import *
class Engine:
	def __init__(self):
		self.loadPlugins()
	def loadPlugins(self):
		self.plugins = {}
		for pluginName in plugins.__all__:
			plugin = getattr(plugins, pluginName)
			self.plugins[plugin.uid] = plugin
	def install(self, selectedPlugins):
	    if not self.confirm(selectedPlugins): return
	    for plugin in selectedPlugins:
	        if plugin.isInstelled(): continue
			for rp in plugin.requiredPlugin:
	            requiredPlugin = self.plugins[rp[0]]
				requiredVersion = rp[1]
				if requiredPlugin.version < requiredVersion: 
					raise Exception()
				self.install([requiredPlugin])
	        for f in plugin.modifiedFiles:
	            self.backup(f)
	        self.installPackages(plugin.requiredRepositories, plugin.requiredPackages)
	        plugin.install()

```[/QUOTE]
EasyUbuntu already has something very similiar, based on a xml file. The file is simple to modify, works well and is tested. 

This is not documented, as we felt that it is not relevant for end users.

---

### Post by russianbandit on 2006-06-01
I've noticed that Automatix installs gstreamer-0.8 stuff while BUMPS gets gstreamer-10.0 stuff. I'd think that the latest stuff is better. Why such difference between the two?

---

### Post by roger6106 on 2006-06-01
[QUOTE=eqisow]From [https://wiki.ubuntu.com/EdgyIdeas](https://wiki.ubuntu.com/EdgyIdeas):

This is awesome and I fully support it, but what do you guys think about just having a single prompt on first boot that ask you if you want to install all multimedia packages and etc?[/QUOTE]

I've always wondered why there isn't a simple first run dialog that asks you about installing multimedia packages, etc.

---

### Post by WildTangent on 2006-06-01
[QUOTE=roger6106]I've always wondered why there isn't a simple first run dialog that asks you about installing multimedia packages, etc.[/QUOTE]
Because for the multimedia codecs that Ubuntu doesn't support, there are license fees. And the DVD codecs aren't even licensed to end-users unless it's through the software of a licenses developer of DVD-playing software like PowerDVD, or WinDVD. Even Windows doesn't have DVD support by default.

-Wild

---

### Post by ago on 2006-06-02
[QUOTE=robotgeek]EasyUbuntu already has something very similiar, based on a xml file. The file is simple to modify, works well and is tested. 

This is not documented, as we felt that it is not relevant for end users.[/QUOTE]
This is exactly my point...

I think you guys are going to converge ANYWAY... 

Because the "framework" required is very similar (plugin based), the language chosen is the same (python) and the underlying scripts are almost identical (there aren't 10 different ways of installing libdvdcss2, you all are doing the same thing...). You might have different tastes about how to package stuff together or on the front-end... But if the plug-in framework is flexible enough everybody can be accomodated within the same "engine"... Differences will be expressed as different plugins/metaplugins and/or different frontends. 

If you all realize this, things could move much faster for everybody and be far less confusing for new users.

But there is more...

While I was thinking about a possible common framework, I also made an interesting discovery... The framework you are converging too already exists... And is called apt. You can in fact think of deb packages as plugins hosting scripts, binaries, and metainfo on the package... Instead of creating a new plugin mechanism, choose a common repository*, package existing scripts as .deb packages. Only then think about the front-end. This will speed things even further...

* In fact the choice of the repository is trivial: it will be either multiverse or restricted or plf according to the status of the dependencies...

---

### Post by ago on 2006-06-02
[QUOTE=WildTangent]Because for the multimedia codecs that Ubuntu doesn't support, there are license fees. And the DVD codecs aren't even licensed to end-users unless it's through the software of a licenses developer of DVD-playing software like PowerDVD, or WinDVD. Even Windows doesn't have DVD support by default.

-Wild[/QUOTE]

Even more importantly because closed codecs/standards/drivers should be actively disincentivized. People should first try open source alternatives, if you foster closed solutions (e.g. by asking at startup to install proprietary codecs) you will strangulate the open standards and society as a whole will be worse off. Standards are good, open standards are better, monopolies are based on network externalities which in turns are based on legal/technical incompatibilities. Open standards kill network externalities, network externalities kill open standards. But in order to spread open standards critical mass is needed, and in order to reach critical mass you have to overcome the chicken and egg problem. The point is that people should: 

1) understand the legal situation, implications for society... 

2) try to foster open standards whenever possible (e.g. requiring friends not to send them word documents or wmp files, save your music as ogg, buy ogg compatible players, avoid drm, no skype, no closed IM...)

3) since there might be situations when closed solutions are still required (unless you are called Richard), make it still possible to use them, but not before you explain the points above so that people will use the closed solutions only when strictly necessary and will not contribute to spreading them farther...

Therefore the best solution to me is a dialog appearing when you try to use something which requires "closed" software [http://www.ubuntuforums.org/showpost.php?p=1076911&postcount=20](http://www.ubuntuforums.org/showpost.php?p=1076911&postcount=20)

And this is also a reason why I am in favor of wrapping scripts as debian packages, because they will be easier to integrate with the "explanation dialog"...

---

### Post by ago on 2006-06-02
[QUOTE=robotgeek]
This is not documented, as we felt that it is not relevant for end users.[/QUOTE]

I think that it would help if you had a section for developers quickly explaining the framwork and how to extend easyubuntu.

Even more importantly, it would help if in the wiki you explained what each "action" does exactly and how to replicate the same behaviour manually. This would also foster cooperation, it would help checking the scripts, it would be educational and useful for how-to/guides, improve the confidence of more paranoid users.

---

### Post by ago on 2006-06-02
[QUOTE=ago]I found this interesting thread: 
[http://www.ubuntuforums.org/showthread.php?t=177858](http://www.ubuntuforums.org/showthread.php?t=177858)[/QUOTE]

Other interesting links on the subject:

[https://wiki.ubuntu.com/RestrictedFormatsProblem](https://wiki.ubuntu.com/RestrictedFormatsProblem)
[https://wiki.ubuntu.com/RestrictedFormatsSolutions](https://wiki.ubuntu.com/RestrictedFormatsSolutions)
[https://wiki.ubuntu.com/EasyCodecInstallation](https://wiki.ubuntu.com/EasyCodecInstallation)
[https://wiki.ubuntu.com/RestrictedFormatsAssistant](https://wiki.ubuntu.com/RestrictedFormatsAssistant)
(I am in favor of the EasyCodecInstallation proposal)

For all other Edgy propasals:

[https://launchpad.net/distros/ubuntu/+roadmap](https://launchpad.net/distros/ubuntu/+roadmap)
[https://launchpad.net/distros/ubuntu/+specs](https://launchpad.net/distros/ubuntu/+specs)

---

### Post by elamericano on 2006-06-02
Regarding EasyUbuntu being available for Dapper, has anyone actually looked at how little it does on Dapper? I'm sure it'll add more later, but for now it's comaparable to BUMPS. I'd run BUMPS instead at this point.

---

