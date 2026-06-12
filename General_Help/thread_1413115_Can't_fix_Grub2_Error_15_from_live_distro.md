---
title: "Can't fix Grub2 Error 15 from live distro"
date: 2010-02-22
forum: General Help
---

### Post by freddiespagheti on 2010-02-22
Well, I've made a nice mess.

I was messing around updating grub and I skipped a step or something else went wrong and now I can't boot. I get Grub error 15

So, being on a netbook (AA1), I can't use a live cd and right now I'm running Puppy Linux off of a really small flash drive.

I pulled up this tutorial on how to fix it.
[URL="https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found"]https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found
[/URL]
and everything went fine until 

```

dpkg-reconfigure grub-pc
```The first two steps work find and then I get:

```
mkdir: cannot create directory '/boot/grub': Operation not permitted

```Any ideas?

My guess is that Puppy Linux doesn't have the Grub files to fix it maybe? I wouldn't really know.

Any ideas? I'm looking for a solution that would not involve me making another live usb because that's a little difficult for me at this point. I could if I had to though.

---

### Post by Jackzor on 2010-02-22
I think you will need to get The "Ubuntu liveCD" and use it. Like the Tut. says. I don't know alot about commands but I'm betting the commands you are using are alittle different from the puppy linux commands that you are using.

---

