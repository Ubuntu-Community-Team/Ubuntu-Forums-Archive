---
title: "changed fstab now cant even boot into recovery"
date: 2010-09-01
forum: General Help
---

### Post by ICANSEEYOU7687 on 2010-09-01
I followed this
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

and instead of a fat32 I added a ntfs 2 tb hd to my computer. But it doesnt like it, so now when I boot I get

init: ureadahead-other main process (1234) terminated with status 4

I searched and people are mentioning logging into the terminal and what not, but I cant get to a terminal so that kind of silly.

People also talking about updating their video cards for this issue, which also is not my problem.

But it does the same thing in recovery too, and I dont know what to do, please help!

---

### Post by oldfred on 2010-09-01
Do you have a liveCD. Then you can get to a terminal.

What changes did you do to fstab. Did you run the sudo mount -a as the instructions say, as that would tell you if you made an error that would prevent you from booting.

From liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by ICANSEEYOU7687 on 2010-09-01
Yea, I changed them back, but the error is still there.  So it thought it was the NTFS configuration utility automouting it, so I commented those same lines.  Same error.

Now  I dont know what to do.  Is there anything I can do but reinstall?  Can I reset the files abck to the stock somehow?  Ugh ive spent so much time setting this up the past few days I really dont want to have to format the machine.  Although its my own damn fault for not making a bakup fille.  But if someone could help me i would REALLY appreciate it

---

### Post by CharlesA on 2010-09-01
Does hitting "s" do anything?

---

### Post by ICANSEEYOU7687 on 2010-09-01
yes! Thank you!  I feel silly about not knowing that I could do that.  Now is there any way I can restore all of my mounting information to the originals?  So basicallly to just mount the system drive, and nothing else.

I think it might be more then my fstab ><

*EDIT* AHHH I fixed it, thanks so much for yalls replies.  Im definately getting into the habbit of backing up files before I mess with them, haha, thanks all!

---

