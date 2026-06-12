---
title: "OpenOffice Open/Save extrmely slow"
date: 2010-06-18
forum: General Help
---

### Post by SwedishWings on 2010-06-18
Often when i open a document in writer (local or on NFS shares), OpenOffice hangs for like 10 to 30 seconds, and then resumes without problem. 

I'm on Lucid using the standard OpenOffice 3.2 installation, no add ons or so.

Has anyone experienced this as well? Any help is most welcome!

Thanks,
Mike

---

### Post by robert shearer on 2010-06-18
same here,    may just be "normal" perhaps.

---

### Post by shahan on 2010-06-18
Have u made any change to the settings of OpenOffice? I am also using Lucid. There has no problem at all. Its working fine. I am working regulrly on OpenOffice for about a month when Lucid has been released. Whats ur computer configuration. Is it enough fast to run ur PC?

---

### Post by SwedishWings on 2010-06-18
> **robert shearer said:**
> same here,    may just be "normal" perhaps.
I think there is a timeout of some sort, maybe network related. OO loads in less than 5 seconds on my box, why should it take 30 seconds to load a document? Something must be wrong.

---

### Post by SwedishWings on 2010-06-18
> **shahan said:**
> Have u made any change to the settings of OpenOffice? I am also using Lucid. There has no problem at all. Its working fine. I am working regulrly on OpenOffice for about a month when Lucid has been released. Whats ur computer configuration. Is it enough fast to run ur PC?

No changes made what so ever. 

I'm running on MacBook 5,1. When OO is "hanging" during load/save, CPU load is less than 5%, so i guess it is some kind of timeout.

---

### Post by SwedishWings on 2010-06-18
Just tried to disconnect the network cable, and guess what - it loads any document in a fraction of a second. This really appears to be some kind network related timeout.

---

### Post by robert shearer on 2010-06-18
> **SwedishWings said:**
> Just tried to disconnect the network cable, and guess what - it loads any document in a fraction of a second. This really appears to be some kind network related timeout.

Well how about that then !. 
Just to confirm that this does indeed work.

---

### Post by philinux on 2010-06-18
Are you guys using a proxy?

---

### Post by robert shearer on 2010-06-18
> **philinux said:**
> Are you guys using a proxy?

Not that I know of. How would I check ?

Edit,   from wikipedia > Intercepting proxies are also commonly used by ISPs in some countries to save upstream bandwidth and improve customer response times by caching. This is more common in countries where bandwidth is more limited (e.g. island nations) or must be paid for.


Well New Zealand is both an island nation and we do pay for allocation/Mb so it may apply. Must check with ISP.

Though,  why would Open Office be trying to access the web when I am opening local documents ??  Seems rather 'odd' behavior.

---

### Post by Tombgeek on 2010-06-18
I have experienced it as well. It is really annoying.
I downloaded OpenOffice 3.2.1 and uninstalled the default OpenOffice 3.2.0, but it still takes too long.

What is the issue? All I want to do is write a <snip> novel without issues, is that so much to ask?
I'm using Abiword in the meantime, until Oracle fixes the issues.

---

### Post by Tombgeek on 2010-06-18
> **robert shearer said:**
> Not that I know of. How would I check ?

Edit,   from wikipedia 

Well New Zealand is both an island nation and we do pay for allocation/Mb so it may apply. Must check with ISP.

Though,  why would Open Office be trying to access the web when I am opening local documents ??  Seems rather 'odd' behavior.

[IMG]http://evanbroderick.files.wordpress.com/2009/09/tinfoil-hat1.jpg[/IMG]

---

### Post by philinux on 2010-06-18
Try these tweeks.

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

---

### Post by robert shearer on 2010-06-18
> **philinux said:**
> Try these tweeks.

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

Well, it **runs** faster as per the link tweaks but won't load files any faster so problem remains the same.

While the file is being loaded(or waiting to be loaded) there are several activity spikes for the network as viewed in Gnome system monitor.

As SwedishWings pointed out this causes a timeout and slows file loading.
Disconnect or disable networking and files load fast.

So, is that indicative of some sort of database lookup (that we can disable. I cannot find anything in OOorgs options), or a sync to something like Ubuntu One, or is it something more sinister ?? 

Of course the fix is to never be online when using Open Office but its not too practical.

---

### Post by SwedishWings on 2010-06-18
> **philinux said:**
> Try these tweeks.

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

This made no difference for me at all. 

I spent a fair amount of time searching for a solution, but failed. Strange that it only affects some users.

---

### Post by philinux on 2010-06-18
> **SwedishWings said:**
> This made no difference for me at all. 

I spent a fair amount of time searching for a solution, but failed. Strange that it only affects some users.

Very odd. OO opens in less than 2 seconds here.

Double check in system>network proxy.

Try running it from a terminal see if there are any messages.

```
ooffice -writer 
```

---

### Post by SwedishWings on 2010-06-18
> **philinux said:**
> Are you guys using a proxy?

nope. i'm having the same issue both at home and at my office, with two different operators, so it seem to be network independent.

---

### Post by SwedishWings on 2010-06-18
> **philinux said:**
> Very odd. OO opens in less than 2 seconds here.

Double check in system>network proxy.

Try running it from a terminal see if there are any messages.

```
ooffice -writer 
```

i tried that, but get no messages at all. is there a debug switch or something for OO?

You said "opens". I mean opening a document, and sometimes when saving. Are we talking about the same thing here?

---

### Post by philinux on 2010-06-18
> **SwedishWings said:**
> i tried that, but get no messages at all. is there a debug switch or something for OO?

You said "opens". I mean opening a document, and sometimes when saving. Are we talking about the same thing here?

Yes, I usually double click on a document. So OO opens itself and opens the doc in a flash.

Might be worth renaming ~/.openoffice.org and let it create a new default profile.

---

### Post by Tombgeek on 2010-06-18
> **robert shearer said:**
> Well, it **runs** faster as per the link tweaks but won't load files any faster so problem remains the same.

While the file is being loaded(or waiting to be loaded) there are several activity spikes for the network as viewed in Gnome system monitor.

As SwedishWings pointed out this causes a timeout and slows file loading.
Disconnect or disable networking and files load fast.

So, is that indicative of some sort of database lookup (that we can disable. I cannot find anything in OOorgs options), or a sync to something like Ubuntu One, or is it something more sinister ?? 

Of course the fix is to never be online when using Open Office but its not too practical.

The same thing happens with OpenOffice 3.2.1
I tried it just now. I disconnected my wired network, and it took a second to load a file.
<sigh>
](*,)
Does anyone know how to fix this?

---

### Post by robert shearer on 2010-06-18
Looking through all the options for OOorg  I get the impression that there is some preload that involves Evolution and am wondering if any of you use or have Evolution on your system ??

I do not use it so purged it (and all the other social networking gubbins too).

I wonder now if this has broken a link that involves OOorg so would be interested to know if you are using Evolution or if this is a commonality that may point to a cause.

Other than that paranoia threatens.  Is Oracle or Canonical or some other 'icle  'acle  collecting usage stats for OOorg. :confused:

Sufficed to say that until it is sorted I won't be online when using Oorg simply on principle.

--Phil, I tried opening in console early on but got no messages.

If it is any help, when this happens there is no extra resource use shown in Gnome monitor (other than network).
However the entire screen greys out (everything else is still responsive and I can open and use other apps while I wait)

The only other time I see the greyed out screen is when I install something from a Deb file.

---

### Post by SwedishWings on 2010-06-19
> **robert shearer said:**
> Looking through all the options for OOorg  I get the impression that there is some preload that involves Evolution and am wondering if any of you use or have Evolution on your system ??

I do not use it so purged it (and all the other social networking gubbins too).

I wonder now if this has broken a link that involves OOorg so would be interested to know if you are using Evolution or if this is a commonality that may point to a cause.


Yes, i use Evolution, but the problem is still there.

---

### Post by SwedishWings on 2010-06-19
Accidentally, i was hooking up on another wireless network yesterday and was surprised to see that the problem was gone while connected in that particular network. 

I have absolutely no idea what the difference was - but the point is that exactly the same configuration seem to work in some networks and not on others.

Could it be a DNS issue? Or that some ports need to be open in order for OO to open/save properly? Either way, OO is doing something that it should not, that's for sure.

---

### Post by Tombgeek on 2010-06-19
> **SwedishWings said:**
> Accidentally, i was hooking up on another wireless network yesterday and was surprised to see that the problem was gone while connected in that particular network. 

I have absolutely no idea what the difference was - but the point is that exactly the same configuration seem to work in some networks and not on others.

Could it be a DNS issue? Or that some ports need to be open in order for OO to open/save properly? Either way, OO is doing something that it should not, that's for sure.

Could be, I have a ADSL connection, so it seems it may be a bug that is only triggured by wired connections.
Does anyone have an account on [www.OpenOffice.org?](www.OpenOffice.org?)
Should I send an e-mail to them and report the bug?

---

### Post by SwedishWings on 2010-06-19
> **Tombgeek said:**
> Should I send an e-mail to them and report the bug?

I would appreciate that, i have no account.

Can this be related to network printers? That's the only thing i can imagine that OO might need to see before loading a document. Why save is slow, still is a mystery though.

---

### Post by Tombgeek on 2010-06-20
> **SwedishWings said:**
> I would appreciate that, i have no account.

Can this be related to network printers? That's the only thing i can imagine that OO might need to see before loading a document. Why save is slow, still is a mystery though.


I created an accout. I am just waiting for an email that will verify my login details.
I did have a look at the Issue Tracker. Someone did mention something about slow saving and loading times, and did mention that it may be a problem that is related to his network printer. But his issue is on Windows XP and I did not check which version of OpenOffice it was. I will get back to you on that one.
No one has mentioned any issue on Ubuntu about slow loading or saving times. But I will search a bit more.

---

### Post by Tombgeek on 2010-06-20
I have sent in an issue report. Hopefully they will get back to me soon.

---

### Post by Tombgeek on 2010-06-21
Are there perhaps any Ubuntu 9.10 users who installed OpenOffice 3.2.0 or 3.2.1 and experienced the same bug?

Here is the report on the OpenOffice.org site:
[http://www.openoffice.org/issues/show_bug.cgi?id=112546](http://www.openoffice.org/issues/show_bug.cgi?id=112546)

---

### Post by SwedishWings on 2010-06-21
Tombgeek, thanks for helping out!

---

### Post by robert shearer on 2010-06-21
> **SwedishWings said:**
> Tombgeek, thanks for helping out!

seconded ! ):P

---

### Post by Tombgeek on 2010-06-21
Hey guys.

So they have gotten back to me (as you can see in the link). It seems they have been able to discover the issue. However, due to the fact I am not too experienced with programming (I only know the basics of Delphi and Pascal, and I don't even know how to do loops and string handling), I have absolutly do idea whatsoever of what this guy is talking about. Perhaps you guys know. His username is "hdu":

> Confirming on Debian for doing the file open dialog. Adjusting the priority as the multisecond hang is 
quite bad. Profiling shows that the culprit seems to be the excessive use of "realpath()" on EACH file of the 
active directory:
- is that level of detail needed when the file name alone should suffice to fill the open/close dialogs?
- why on each file in the directory?Then he placed an attachment:

> #1  ___lxstat64 (vers=3, name=0xfffba140 "/net/hs-eham02-01", buf=0xfffba09c) at sysdeps/unix/sysv/linux/lxstat64.c:48
#2  __realpath (name=0xee6d60f4 "/home/hd114770/tmp/tausch", resolved=0xfffba140 "/net/somehost") at canonicalize.c:162
#3  ?? () libuno_sal.so.3
#4  ?? () from libuno_sal.so.3
#5  osl_getFileStatus () from libuno_sal.so.3
#6  osl::DirectoryItem::getFileStatus(osl::FileStatus&) () from libucpfile1.so
#7  fileaccess::shell::getv(fileaccess::Notifier*, com::sun::star::uno::Sequence<com::sun::star::beans::Property> const&, osl::DirectoryItem&, rtl::OUString&, unsigned char&) () from libucpfile1.so
#8  fileaccess::XResultSet_impl::OneMore() () from libucpfile1.so
#9  fileaccess::XResultSet_impl::next() () from libucpfile1.so
#10 svt::FileViewContentEnumerator::enumerateFolderContent() () from libsvtli.so
#11 svt::FileViewContentEnumerator::enumerateFolderContentSync(svt::FolderDescriptor const&, IUrlFilter const*, com::sun::star::uno::Sequence<rtl::OUString> const&) () from libsvtli.so
#12 SvtFileView_Impl::GetFolderContent_Impl(svt::FolderDescriptor const&, FileViewAsyncAction const*, com::sun::star::uno::Sequence<rtl::OUString> const&) () from libsvtli.so
#13 SvtFileView_Impl::GetFolderContent_Impl(String const&, FileViewAsyncAction const*, com::sun::star::uno::Sequence<rtl::OUString> const&) () from libsvtli.so
#14 SvtFileView::ExecuteFilter(String const&, FileViewAsyncAction const*) () from libsvtli.so
#15 SvtFileView::Initialize(String const&, String const&, FileViewAsyncAction const*, com::sun::star::uno::Sequence<rtl::OUString> const&) ()



---

### Post by Tombgeek on 2010-06-21
> **SwedishWings said:**
> Tombgeek, thanks for helping out!

> **robert shearer said:**
> seconded ! ):P

Glad to help. But I did not even do much. I just sent an issue report.
Plus anyway, I want this problem fixes as much as you guys. I have a novel to write and I do not really like Abiword that much (and manuscript editing in Abiword sucks, I prefer setting up margins and headers in OpenOffice).

Sorry Abiword fans, just my opinion.

---

### Post by robert shearer on 2010-06-21
All beyond me I'm afraid.
Though from the mention of realpath and the line..

> #2 __realpath (name=0xee6d60f4 "/home/hd114770/tmp/tausch", resolved=0xfffba140 "/net/somehost") at canonicalize.c:162

does it refer to this ???

[https://www.securecoding.cert.org/confluence/display/seccode/FIO02-C.+Canonicalize+path+names+originating+from+untrusted+sources](https://www.securecoding.cert.org/confluence/display/seccode/FIO02-C.+Canonicalize+path+names+originating+from+untrusted+sources)

---

### Post by Tombgeek on 2010-06-21
> **robert shearer said:**
> All beyond me I'm afraid.
Though from the mention of realpath and the line..



does it refer to this ???

[https://www.securecoding.cert.org/confluence/display/seccode/FIO02-C.+Canonicalize+path+names+originating+from+untrusted+sources](https://www.securecoding.cert.org/confluence/display/seccode/FIO02-C.+Canonicalize+path+names+originating+from+untrusted+sources)

I don't know.
All that is beyond me as well.

hdu said that the attachment was [FONT=monospace]"[/FONT]typical stack during the multisecond "hang"."

---

### Post by Tombgeek on 2010-06-23
> @mav: I looked into the problem again and the problem seems to be in linux running into a timeout 
when it lstats the automounter part of the realpath() result. So it was not the many lookups that were 
the problem, but the one lookup that timed out. Here is the relevant excerpt from strace, which shows 
the 12sec hang:

14:56:51.25 lstat64("/net", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
14:56:51.25 lstat64("/net/xyz-server-01",  <unfinished ...>
14:57:03.77 <... lstat64 resumed>) = -1 ENOENT (No such file or directory)

Ceterum censeo: realpath() has no value add in the file-open/save scenario that would be worth a 
multi-second hangAlso, on there was some letter from a user. This guy experienced the exact same issues. 
But it is in Dutch, so you guys might not understand.
[http://nl.openoffice.org/servlets/ReadMsg?list=gebruikers&msgNo=10601](http://nl.openoffice.org/servlets/ReadMsg?list=gebruikers&msgNo=10601)

Seems the problem is with etc/hosts file

I don't know, what do you guys think?

---

### Post by Tombgeek on 2010-06-24
> Another piece in the puzzle: There was a soft-link to a file on a dead server in my default-save dir. You 
can reproduce the problem by creating such a soft-link e.g. in the home directory
    ln -s /net/xyz-server-01/somefile ~/
and make sure the xyz-server-01 is a known server that is not available. Doing a file-open in OOo for 
e.g. the home directory then triggers a realpath-lookup of the file on the dead server, which results in the 
hang until the lookup timeouts.

Looks like they found the problem.

---

### Post by robert shearer on 2010-07-04
Thanks for keeping this alive Tombgeek. :D

I have been following it (and your posts) on
 [http://www.openoffice.org/issues/show_bug.cgi?id=112546](http://www.openoffice.org/issues/show_bug.cgi?id=112546)

and hope for a resolution soon.

(bumping for the attention of anyone else affected :)  )

---

### Post by DawieS on 2010-07-05
I am subscribing to this thread, having experienced the same annoying issue.

I am running Lucid on a home network. If the Internet connection is down (eg. unplugging the router from the LAN), there is a delay of about 20 seconds when opening an OpenOffice word document. If the network is disabled, it opens immediately, but then I lose connection to other PC's.

---

### Post by pravindra.kumar on 2010-07-12
I am also having this problem with my LTSP users, i have tried turning JAVA off also but problem is still. There is no more load average on server.

---

### Post by rohitece06 on 2010-07-14
Ok, so I am using OOO-3.2 Kubuntu 10.04 but I did not install openoffice.org-kde package but I did install openoffice.org-gtk. Document opening and saving etc was OK but during drawing Xorg was gorging over my CPU. So I thought its probably because of lack of kde customizations i.e. openoffice.org-kde. So I installed it and then the problem of slow opening, save-as-ing, exporting (anything with dialog box) appeared. While exporting a doc the OOO assistant complained that I dont have openoffice help installed. From this forum I got that this slow down problem is some sort of network or database problem. I thought OOO might be looking for the help. So I installed the help files openoffice.org-help-en-us and voila slow down problem gone although Xorg stills shoots up when I do any drawing related movement but I guess we have a resolution on the slow down issue. Please do let all know if it works for you.

---

### Post by robert shearer on 2010-07-15
> So I installed the help files openoffice.org-help-en-us and voila slow down problem gone 

I checked and those were already installed.
Still, clutching at straws here, I reinstalled.

I can now report that this package has no affect on the slow file opening and closing on **my** system. 

I am  happy that you have noticed an improvement on yours.

---

### Post by Tombgeek on 2010-07-16
> **rohitece06 said:**
> Ok, so I am using OOO-3.2 Kubuntu 10.04 but I did not install openoffice.org-kde package but I did install openoffice.org-gtk. Document opening and saving etc was OK but during drawing Xorg was gorging over my CPU. So I thought its probably because of lack of kde customizations i.e. openoffice.org-kde. So I installed it and then the problem of slow opening, save-as-ing, exporting (anything with dialog box) appeared. While exporting a doc the OOO assistant complained that I dont have openoffice help installed. From this forum I got that this slow down problem is some sort of network or database problem. I thought OOO might be looking for the help. So I installed the help files openoffice.org-help-en-us and voila slow down problem gone although Xorg stills shoots up when I do any drawing related movement but I guess we have a resolution on the slow down issue. Please do let all know if it works for you.

Where can I download it? I downloaded it from the Software Centre, but Writer tells me I still need to download it.

---

### Post by LK_gandalf_ on 2010-07-22
Hi all, I have the same issue since one and half year at least, from Kubuntu 9.04 if I'm not wrong. I stick with Ubuntu only because I like it, I support it, and the issue is random, so luckily it doesn't happen everytime. But productivity sucks a lot. It takes almost 20 seconds to do a save/opening, and every click I do (for example to browse into a sub-folder) takes the same. 
Currently I use Kubuntu 10.04 64bit and the same issue appears on two different laptops. No fix found. I tried disabling java but nothing. 
I hope that someone is able to find a definitive fix....this is really sad.:(

---

### Post by jynyl on 2010-07-24
Similar behaviour here; OOO is very slow to open files, eg to insert a picture from file.  It takes 10 to 15 seconds just to refresh the directory listing in the open file dialog.
Running OOO 3.2 on Kubuntu 10.04 64 bit.  Software off the repositories, no special tweaks.  The previous version of OOO & Kubuntu ran fine on this hardware.

But shutting down OOO and restarting it seems to fix the problem. (?)

---

### Post by CoolJohnB on 2010-07-25
I too had the same problem and seemed to have solved it by changing the path for files as I use a 2nd HD for storing all my Data I pointed Ooo to the appropriate folder for My Documents, on that drive and now files load and save instantly!!  Incedently I also changed the back up folder to my Data drive

---

### Post by cyrus_the_virus on 2010-07-27
> **Tombgeek said:**
> Also, on there was some letter from a user. This guy experienced the exact same issues. 
But it is in Dutch, so you guys might not understand.
[http://nl.openoffice.org/servlets/ReadMsg?list=gebruikers&msgNo=10601](http://nl.openoffice.org/servlets/ReadMsg?list=gebruikers&msgNo=10601)

Seems the problem is with etc/hosts file

I don't know, what do you guys think?

That solution works for me. I added this to my /etc/hosts file
```

127.0.0.1    **hostname** localhost **hostname**.(none)

```
Replace **hostname** with your hostname. (If you don't know what your hostname is you can enter 'hostname' in a terminal)

I did some packet sniffing and found out OO does a DNS query on "hostname.(none)" for some reason.  This host does not exists so it times out. By adding this line to your hosts file your basically saying that "hostname.(none)" is your own machine so a DNS query isn't necessary.

---

### Post by Tombgeek on 2010-07-29
> **cyrus_the_virus said:**
> That solution works for me. I added this to my /etc/hosts file
```

127.0.0.1    **hostname** localhost **hostname**.(none)

```Replace **hostname** with your hostname. (If you don't know what your hostname is you can enter 'hostname' in a terminal)

I did some packet sniffing and found out OO does a DNS query on "hostname.(none)" for some reason.  This host does not exists so it times out. By adding this line to your hosts file your basically saying that "hostname.(none)" is your own machine so a DNS query isn't necessary.

Is that even safe? Won't it affect other system or application software?

---

### Post by SwedishWings on 2010-08-03
> **cyrus_the_virus said:**
> That solution works for me. I added this to my /etc/hosts file
```

127.0.0.1    **hostname** localhost **hostname**.(none)

```
Replace **hostname** with your hostname. (If you don't know what your hostname is you can enter 'hostname' in a terminal)

I did some packet sniffing and found out OO does a DNS query on "hostname.(none)" for some reason.  This host does not exists so it times out. By adding this line to your hosts file your basically saying that "hostname.(none)" is your own machine so a DNS query isn't necessary.

Yes, it worked for me as well. At first, I left out the ".(none)", but after adding that it worked. Thanks a lot for this fix!

---

### Post by Tombgeek on 2010-08-04
> **SwedishWings said:**
> Yes, it worked for me as well. At first, I left out the ".(none)", but after adding that it worked. Thanks a lot for this fix!

How do I change it?

Ubuntu won't allow me to change the file, even though I am the computer's administrator.

---

### Post by SwedishWings on 2010-08-04
> **Tombgeek said:**
> How do I change it?

Ubuntu won't allow me to change the file, even though I am the computer's administrator.

Try this:

Open Applications->Accessories->Terminal

and at the terminal enter

[INDENT]sudo gedit /etc/hosts[/INDENT]

Hope this helps.

---

### Post by Tombgeek on 2010-08-04
> **SwedishWings said:**
> Try this:

Open Applications->Accessories->Terminal

and at the terminal enter
[INDENT]sudo gedit /etc/hosts[/INDENT]Hope this helps.


You're my new best friend :D

Woooooooooooooooooooooooooo! It's working!!!!!!!

Okay, so just a summery on the solution.

Open Applications->Accessories->Terminal

Then type 

> 
sudo gedit /etc/hosts


Then edit the file so it looks like this:

127.0.0.1    localhost
127.0.1.1    hostname
127.0.0.1    **hostname** localhost **hostname**.(none)


I actually feel so stupid that I did not try to read that letter in dutch, because I know a bit of Afrikaans.  *facepalm*

"Het resultaat is waanzinnig goed! Ik ben blij."
<sigh> 
I confuse myself as to why I do certain things.

---

### Post by SwedishWings on 2010-08-04
> **Tombgeek said:**
> Then edit the file so it looks like this:

127.0.0.1    localhost
127.0.1.1    hostname
127.0.0.1    hostname localhost hostname.(none)


Happy to help :D

I think the first line should be deleted, so it will be:

```
127.0.1.1    **hostname**
127.0.0.1    **hostname** localhost **hostname**.(none)

```

This is what I have now, and it works.

---

### Post by c69 on 2010-09-08
THIS IS STILL BROKEN

I have changed /etc/hosts and still have the problem.


THe saves take exponentially longer depending on how big the file is.  Using just standard text, no pictures or embedded content.

When a document has nothing in it, saves are almost instantaneous.

When a document is in the 50 page range, a load/save will take 45s.


There must be another variable, that has not been controlled.  Ubuntu 10, latest version of OO.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
OK, here is a workaround.

The issue is with the file dialogs in KDE in particular, and possibly Gnome.  The workaround is to have OOo use its own, rather spartan, file dialogs.

Tools | Options | General tab

In the middle on the left side, check the box "Use OpenOffice.org dialogs"

All the delays go away.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559"), message 12.

Hopefully the next update to KDE will fix this, as it makes the use of OOo almost impossible.

Frank.

---

### Post by chip616 on 2011-01-20
Try this:

Tools | Opetions | General tab

In the middle on the left side, check "Use Openoffice.org dialogs"

Now try it.  Has the delay gone away?

OOo dialogs are very spartan, but on my machine (Kubuntu 10.04 - OOo 3.2.0) this cleared up the delay immediately.  Gnome may have similar issues.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559") message 12.

Frank.

---

### Post by chip616 on 2011-01-20
Try this:

Tools | Opetions | General tab

In the middle on the left side, check "Use Openoffice.org dialogs"

Now try it.  Has the delay gone away?

OOo dialogs are very spartan, but on my machine (Kubuntu 10.04 - OOo 3.2.0) this cleared up the delay immediately.  Gnome may have similar issues.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559") message 12.

Frank.

---

### Post by chip616 on 2011-01-20
Try this:

Tools | Opetions | General tab

In the middle on the left side, check "Use Openoffice.org dialogs"

Now try it.  Has the delay gone away?

OOo dialogs are very spartan, but on my machine (Kubuntu 10.04 - OOo 3.2.0) this cleared up the delay immediately.  Gnome may have similar issues.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559") message 12.

Frank.

---

### Post by chip616 on 2011-01-20
Try this:

Tools | Options | General tab

In the middle on the left side, check "Use Openoffice.org dialogs"

Now try it.  Has the delay gone away?  If so, the issue is not with OOo at all, but with the desktop environment.

OOo dialogs are very spartan, but on my machine (Kubuntu 10.04 - OOo 3.2.0) this cleared up the delay immediately.  Gnome may have similar issues.

Much thanks to the fellows in the [Compuserve Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=130559") message 12.

Frank.

---

### Post by chip616 on 2011-01-20
OK, sorry for the multiple posts.

The forum was not accepting replies a couple of hours ago.  I tried several times to answer this thread.  As you can see, they all came through at the same time.  :(

I'd delete some of those copies, but I don't know if it is possible in this forum.

Frank.

---

### Post by robert shearer on 2011-01-20
Thanks for your workaround suggestion..

Unfortunately it did not work for me.(Gnome desktop)
 open/save still slow.

---

### Post by chip616 on 2011-01-20
Robert:

Too bad it didn't work.  However, this does highlight the fact that there are several issues going on here.  They all have the same result, but obviously there are different causes.

I tried all the previous suggestions as well, and none of them solved it for me.

Hope you get a solution for yours.

Frank.

---

### Post by davemc on 2011-03-21
I've had the same slow open/save issue, same platform Lucid/Kubuntu/AMD64 as reported on OOo 3.2.0.

I tried the hosts fix, and **it worked**, thanks. Rather than .(none), i used a more formal format for /etc/hosts

```

127.0.0.1       localhost.localdomain           localhost
127.0.1.1       myhostname.mydomain.co.nz       myhostname

```

Perhaps the .(none) is a synonym in OOo for the domain of the localhost that never gets populated.

---

