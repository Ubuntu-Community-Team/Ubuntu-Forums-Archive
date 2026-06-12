---
title: "Help! Installed libstdc++6_4.5.0 and broke system..."
date: 2010-06-02
forum: General Help
---

### Post by WestCoastSuccess on 2010-06-02
Need help, badly. I was trying to get iron-linux to run on my 64-bit Hardy system. It was complaining that it required a newer version of libstdc++.so.6. So I attempted to install libstdc++6_4.5.0-4ubuntu1_amd64.deb. The package manager told me I needed gcc-4.5-base_4.5.0-4ubuntu1_amd64.deb, so I installed that first, then went back and installed libstdc++6_4.5.0-4ubuntu1_amd64.deb.

Now my system is _really_ borked! Apt-get doesn't work. Synaptic doesn't work. Partition manager doesn't work. Might be more efficient to list what still _does_ work...

The change to libstdc++.so.6 changed the file /usr/lib/libstdc++.so.6.0.9 to /usr/lib/libstdc++.so.6.0.14 and the link /usr/lib/libstdc++.so.6 now points to that newer file (it previously pointed to ...6.0.9).

I've downloaded what I think are the original Hardy versions of gcc-base and libstdc++ but I cannot install them, as none of the package managers respond (seems they rely upon libstdc++.so.6.0.9).

I searched my system to see if there were copies of the older version lying around and found one in /usr/lib32, but of course that throws up an ELF error when I copy it to /usr/lib since it's the 32 bit version.

I would really appreciate any help - how can I revert to my prior, functioning state? If someone were to send me a copy of libstdc++.so.6.0.9 and I copied it to /usr/lib and changed the link /usr/lib/libstdc++.so.6 to point to it, would that be enough to get Synaptic etc working?

As for iron-linux, shall stop monkeying around and stick to chromium...

Thanks!

---

### Post by WestCoastSuccess on 2010-06-02
OK, looks like I fixed it. Here's what I did in case anyone else gets in this (rather terrifying) situation:


[LIST]
[*]On another computer, I downloaded libstdc++6_4.2.4-1ubuntu4_amd64.deb from [here]("http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.2/") and saved it to the desktop (do not use package manager to install it!).
[*]I used archive manager to explore the file. There were 3 files: "data.tar.gz", "control.tar.gz" and "debian-binary". I double-clicked "data.tar.gz" and it opened with another instance of archive manager. This showed a single folder called ".", which I double clicked to reveal a folder called "usr". Another double-click showed 2 folders: "lib" and "share". Double-click on "lib" brought me to what I wanted - 2 files: "libstdc++.so.6.0.9" and "libstdc++.so.6".
[*]I extracted "libstdc++.so.6.0.9" to my desktop.
[*]I emailed "libstdc++.so.6.0.9" to the problem computer.
[*]On the problem computer, I copied "libstdc++.so.6.0.9" to /usr/lib/
[*]In a terminal, I created a symbolic link to "libstdc++.so.6.0.9" in /usr/lib via sudo ln -s /usr/lib/libstdc++.so.6.0.9 /usr/lib/libstdc++.so.6
[*]I tested apt-get in a terminal: sudo apt-get update. It worked!
[*]To be sure I had everything set up properly, I downloaded libstdc++6_4.2.4-1ubuntu4_amd64.deb from the link above to the problem computer, then installed it from the terminal via: sudo dpkg -i libstdc++6_4.2.4-1ubuntu4_amd64.deb
[*]Tried Synaptic, and it works. Tried Update Manager; also works.
[/LIST]
Here's hoping if you run into this problem the above instructions help.

Double-check that the link /usr/lib/libstdc++.so.6 points to the correct file (which should be /usr/lib/libstdc++.so.6.0.9) and not any other version you may have installed which got you into this situation.

Note too that "6.0.9" applies to Hardy - other Ubuntu distributions likely have different versions - for example my laptop, which runs Lucid, has "6.0.13".

---

### Post by rrnwexec on 2010-06-08
Fret no more! Have you considered joining the Ubuntu Vancouver LoCo? We have hundreds of people who *get* Ubuntu.

It's easy: [http://meetup.com/ubuntuvancouver](http://meetup.com/ubuntuvancouver)

Cheers,
Randall
Ubuntu Vancouver Buzz Generator

---

### Post by WestCoastSuccess on 2010-06-08
Many thanks for the invitation, but unfortunately (and under protest, I should add) I am moving to Toronto Aug 1st.

But your suggestion has prompted me to find an Ubuntu group in TO - thanks!

Good luck with the Vancouver group!

---

