---
title: "SVN hosting for me and friends."
date: 2011-06-11
forum: General Help
---

### Post by simolokid4 on 2011-06-11
Dear Ubuntuforums,

Recently I've had the joy of creating dozens of svn repo's for myself for all my idea's i'd like to work out.

Now my friend has some ideas too, and since I'd like the practise of keeping my vps configured while he can also work on it I came here, since I have no clue where to begin here. (Practising my linux skills, specifiqly ubuntu.. always fun ! )

' So.. what the hell do you want ?.. '

Basicly I'm planning on writing a back-end in php to manage members that can use my svn on my vps. In this back-end I can invite people to join the service for free.

Then when they accept the invite I'd like for them to login and be able to create their own repo's.

I've already planned out how I'm going to adjust websvn to let them see their own projects only and not anyone else's.

So basicly my question is this;

Where do I even begin to make my friend(s) capable of creating their own repos from a php webpage on my vps?

I tought something among the lines of:
- Using the php svn_create_repo method, but its experimental.. I'd like it all to be stable.
- Creating a cronjob that will walk trough all folders in this webdir and see if there are empty ones, where there are, create a repo with the name from the single file in that dir. Where the name of the user would correspond to the name of the root folder of that user. This way it wouldnt be instant and it wouldnt be user friendly, but it ... could.. work.. =p

I'm absolutely convinced there are easyer ways of doing this... I just can't seem to wrap my head around it.

Could someone be so kind to give me some pointers?

I am going to do all the php coding myself, and am comfortable with vim / editing stuff on vps.

Thanks a lot for any ideas.

---

### Post by simolokid4 on 2011-06-12
Ugh.. aparently its a lot easyer then i Imagined...

Just tought to google 'create svn repo from php script' and ran into 
[http://www.tamdenholm.com/portfolio/svn;](http://www.tamdenholm.com/portfolio/svn;)

This looks like something Im able to do !

---

