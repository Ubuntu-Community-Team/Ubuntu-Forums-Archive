---
title: "Ubuntu License"
date: 2009-11-16
forum: General Help
---

### Post by jonnytabpni on 2009-11-16
Hi Folks,

Can someone please give me some help on the licensing implications of Ubuntu?

I have made a "master disk image" to reimage lots of PCs on a customer's site. This disk image has my business logo as the background. Under the Ubuntu license, do I have to make my logo "open source" as well? Or does that only apply to Ubuntu itself, if I modify the orignal Ubuntu code?

Thanks

---

### Post by jbrown96 on 2009-11-16
you only need to release code if you re-distribute it. You are and must give written offers to get source code to your users. Check out the GPLv2. If you are only replacing logos, then no, they don't need to be open-source. However, you need to worry about trademark infringement. You cannot replace the Ubuntu logo and leave other Canonical trademarks. Check out [this]("http://www.ubuntu.com/aboutus/trademarkpolicy")

The problem that you run into is the commercial nature of your modifications. Canonical generally does not allow minor modifications for commercial distribution.

You should contact Canonical or an attorney. No one on these forums is authorized or capable of giving you a good answer.

---

### Post by jonnytabpni on 2009-11-17
Hi jbrown96, thanks for your response.

Phew, it's such a relief that I can still protect my logo. I do not want people distributing this disk image with my company logo on it (That's OK via the general Ubuntu license isn't it?).

I have no problems offering to give away the source code.

As far as the Ubuntu transmark it concerned, what kind of trademark infringment could their be? At present, all there is is that my company background is on my customer's desktop PCs (I am leasing them out computers). I understand the Cononical may not want their logos on the product, but I can remove them can't I?

It would be nice to still have the Ubuntu logo as the boot splash etc, as I am a huge Ubuntu fan and want to promote their software, however I understand that they may not want this due to the commerical nature of what I'm doing.

Further Info: The disk image contains desktop lockdowns using gconf-editor, pessulus, and my editing the nautillus xml files. Does this have any further implications?

Thanks

---

### Post by audiomick on 2009-11-17
I think jbrown's suggestion was a good one: get in touch with Canonical directly. From the sounds of what you are doing, maybe you could think about becoming a Partner.
[http://www.ubuntu.com/partners](http://www.ubuntu.com/partners)

---

### Post by jbrown96 on 2009-11-17
I'm not entirely sure that you understand the Trademark issue. Trademarks are allowed because they prohibit competitors from releasing a product that could be confused for another. The question you have to ask is: would a reasonable person, running my version of Ubuntu, think that it is the same Ubuntu released by Canonical? If you put some sort of logo on the CD and desktop, I would a say a reasonable person could tell that the two are separate. 

I'm not sure how many Canonical trademarks show up in Ubuntu (I use Kubuntu), so you may have to replace some other icons. Canonical should be able to provide you with a list of things that need to be changed. 

Your logos would certainly not be covered by the GPL, so you retain complete control. 

Your modifications would most likely fall under the GPL, so others could use them. Since you are distributing this disk, you must allow the recipients of the software access to the source code. Note: you don't need to give the general public access, just the people you give the software. The modifications you have made are really tough to define. Usually software is compiled to machine language, which is completely unreadable by people. However, the changes you seem to make, are to text-based configuration files. It would seem that since your modifications are in plain text, you are already giving them the source code. Gconf settings are just GUIs that make changes to config files. 

Here's what I would do:

1) Place a text file on the desktop, put a note on the desktop wallpaper, or put a note on the CD label to the effect of > This software is licensed under the GPLv2. You may receive a full copy of the license by visitng [http://www.gnu.org/licenses/licenses.html#GPL](http://www.gnu.org/licenses/licenses.html#GPL) or by writing to the Free Software         
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

Source code is available upon request from...


2) Put another note stating that > This product is not endorsed, supported, or guaranteed by Canonical Ltd.

3) Do a "diff" of your spin of Ubuntu vs. the official one. Any files that are different must be accounted for. Store a copy of them on your server. Whoever the owner of a program or file is has the responsibility to honor source code requests. Let's say you install VLC on your version, so your customers don't have to; you don't need the source code for that -- VideoLan (VLC's community) will provide it. You just need the code for the modifications you made. This is probably just config files, but play close attention if you compile anything. You don't need to distribute the code to it, provided you don't link to any gpl'd libraries. 

4) Relax! We are not out to get you. You are not going to get your pants sued off if you do violate the gpl. The FSF is much more concerned about cooperation; they want to fix the problem, not profit off of it. Read this excellent [blog entry]("http://ebb.org/bkuhn/blog/2009/11/08/gpl-enforcement.html") by a "gpl enforcer."

5) After you get compliance mostly in order (mostly the disclaimers and gpl notifications), contact Canonical. Send them a picture of your CD, take some screenshots, etc. From the way their website sounds, they should be very reasonable to work with. There are many derivations of Ubuntu; there are probably more than just technical reasons why so many projects use it!

---

### Post by fluffman86 on 2009-11-17
The way I see it, if you are *LEASING* the computers that Ubuntu is on, then you still own the computers.  And you only have to redistribute gpl source code if you make changes to gpl code for something that is being redistributed.  If you are not giving out your CD/images, but only putting it on *YOUR* hardware, then you don't have to do anything.  You are simply modifying and customizing Ubuntu.

Now if you were making huge sweeping changes that completely changed the desktop experience of Ubuntu, then you might consider renaming it and creating a different distrobution or remix.  Contact Canonical about that.  

IANAL, YMMV.

---

### Post by jbrown96 on 2009-11-17
> **fluffman86 said:**
> The way I see it, if you are *LEASING* the computers that Ubuntu is on, then you still own the computers.  And you only have to redistribute gpl source code if you make changes to gpl code for something that is being redistributed.  If you are not giving out your CD/images, but only putting it on *YOUR* hardware, then you don't have to do anything.  You are simply modifying and customizing Ubuntu.

Now if you were making huge sweeping changes that completely changed the desktop experience of Ubuntu, then you might consider renaming it and creating a different distrobution or remix.  Contact Canonical about that.  

IANAL, YMMV.

No. He said that he was using his custom-Ubuntu disk to image computers at a client's office. That's distributing.

---

### Post by fluffman86 on 2009-11-17
> **jonnytabpni said:**
> (I am leasing them out computers).
^

---

### Post by jonnytabpni on 2009-11-18
Folks,

Thanks for all the comments and the reassurance. I have indeed contacted Cononical and I'm just awaiting a reply. 

The 2 things I'm concerned about:

1) Just my business logo - I woudn't be keen on getting that distributed outside of this clients office. As for the Ubuntu disk/code, I'm more than happy to give away the customised versions to anyone that wants it, whether in source or binary, as long as my company logo isn't in the copy. How does this sound?

2) As for the Ubuntu branding, I would actually like the Ubuntu branding to stay as I'm a huge fan of this software (I've got the fleece, mug and mousemat!) however I appreciate it if Cononical want it removed, and of course I'll respect that.

3)In terms of distribution only the "modified bits", by creating user accounts and adding passwords to that, this doesn't constitute as a "modification" does it? I wouldn't want to give the disk image away with our passwords in it! (Keeping the modified config files shouldn't be a problem.

What does everyone else make about the leasing issue? What I have done is:
1) Installed the standard distro of Ubuntu on a "Master PC"
2) Created an unprivledged user
3) Installed some VOIP software (Twinkle)
4) Editing the nautillius xml files, gconf-editor and pessulus to lock down this user to only allowed them access to Twinkle and Firefox.
5) Imaged the partition using partimage
6) Deployed the image on multiple PCs which we own
7) Installed them on a customer site for them to use

No source code as been modified (Heck, I don't even know how to compile any linux stuff!)

Also, the thought of becoming a Cononical partner excites me!! You guys have no idea how much I love Ubuntu. I spent a lot of time on the phone trying to sort out licensing issues with a company that make a "prominent closed-source OS" and my goodness, I'm not even keen on their OS to being with, what they told me after that was just the icing on the cake!  

In the future, my business will want to include some non-free software in this partimage image (Our customer will have bought licenses for this software). What implications does this have? Ovbiously, being non-free software, distribution of the image would not be allowed if it contained this paticular non-free software.

Thanks

---

### Post by jonnytabpni on 2009-11-20
bump :)

---

### Post by jonnytabpni on 2009-11-23
Folks,

I'm thinking of giving the following information to my customer who rents computers from me. What do you think? Is it legal under the GPL?

#Start GPL info

Some of the software distributed to you as part of your agreement with <my business name>, has been licensed by the respective copyright holden under the GPL V2 license. You may receive a full copy of the license by visitng [http://www.gnu.org/licenses/old-licenses/gpl-2.0.html](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html) or by writing to:

The Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA

Please note that while <my business name> retains ownership of the computers provided under the lease agreement, GPL and other open-source licensed software does not fall under this lease agreement. This means that you are the licensee of said software and are entitled to the following things:

1) Corresponding source code of any GPL software running on those machines.
2) To redistribute the GPL'ed binaries to your hearts content, as long as you remain in compliance with the respective GPL agreement.
3) To modify the source code to your hearts content, provided you remain in compliance with the respective GPL agreement.

Please note that while the GPL license entitles you to the above, the following restrictions have been put into place regarding the leased computers which fall under your agreement with <my business name>:

1) Any software or firmware installed on the leased computers must be chosen, installed and configured by <my business name> engineers. You are prohibited from changing any software running on those machines without prior agreement. This does not affect your right to modify the software running on the machines, as long as you make and execute your modifications on a computer which does not fall under your lease agreement with <my business name>.
2) "<my business name>" and the <my business name> logo are registered trademarks. While you are free to modify and/or redistribute GPL'ed software, this does not include the words "<my business name>" or the <my business name> Logo. To put it simply, if you wish to redistribute the software running on the leased computers outside of your organisation, we ask that you remove both of those trademarks. 

Download Links:

Source Code: 
- Orignal Operating System source before <my business name> modifications
- Twinkle VOIP Softphone
- Pessulus Lockdown Editor
- <my business name> "diffs"

Images:
- Orignal ISO (no <my business name> modifications)
- Hard Disk image deployed on all leased computers (Includes <my business name> modifications and trademarks for use within your organisation)
- Hard Disk image deployed on all leased computers with <my business name> modifications but with trademarks removed


#End GPL info

I appreciate your comments

Cheers,

Jonny

---

### Post by jbrown96 on 2009-11-24
That seems reasonable. I'm not sure that the #1,#2,#3 explaining the GPL are really necessary. You could probably get more professional language from the FSF that they would let you use. 

It looks good. I doubt you would every have any trouble with this sort of notice.

---

### Post by jonnytabpni on 2009-11-25
Hi jbrown96,

Thanks for your response

Since I am restricting what can be installed on my machines, the FSF my refer to this as "Tivoisation". GPL2 does not restrict this however GPL3 does.

If I were to use GPL3 code, do you reckon that my restricting my machines would be called Tivoisation? Or does this not apply since I *own* these machines? And also, they software hard disk image could probably be installed on other systems - I don't think Linux has the HAL issues that Windows XP has...

Thanks

---

### Post by jonnytabpni on 2009-11-29
> **jbrown96 said:**
> That seems reasonable. I'm not sure that the #1,#2,#3 explaining the GPL are really necessary. You could probably get more professional language from the FSF that they would let you use. 

It looks good. I doubt you would every have any trouble with this sort of notice.

Hi Folks,

To comply with GPL v3, I'm thinking of changing 1) in the above to the following:

> 
1) Any software or firmware installed on the leased computers must be chosen, installed and configured by <my business name> engineers to qualify for software support services under your maintenance contract. While you are not prohibited from installing, changing, modifying, reconfiguring or removing any software running on the leased computers, doing so will make the respective machine void from <my business name> software support services unless you have agreement with us before you make such alterations. Administrator passwords are available upon request from <my business name> without cost. This does not affect any hardware support services.


---

