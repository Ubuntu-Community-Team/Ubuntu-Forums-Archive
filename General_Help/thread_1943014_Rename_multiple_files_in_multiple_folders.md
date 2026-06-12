---
title: "Rename multiple files in multiple folders"
date: 2012-03-18
forum: General Help
---

### Post by HiImTye on 2012-03-18
ok, so here is the situation.
I have my mp3 collection in multiple folders, in the following order, like a good little penguin:
```
MP3s/<Artist>/<Album>/<Track> - <Title>(.mp3)
```some of them have the .mp3 extension (ones added to my library from other sources, since reformatting my drive) while others do not (ones added to my library, from my iPod, after reformatting my drive).

inside some of these folders are album art and some other stuff, added by Rhythmbox or Banshee or whatever. Banshee only detects the files with the .mp3 extension (so the files from my iPod, added via Rhythmbox do not appear in my library).

I need an easy way to rename files from multiple folders, while excluding the other media types. currently Nautilus does not allow you to select multiple files and rename them.

any help is much appreciated

---

### Post by Karlchen on 2012-03-18
Hello, HiImTye.

If you were on Windows, my advice would definitely be: use Total Commander to do the job. It has got a powerful "multirename tool" functionality. Also in your special case, combining the "branchview" mode with the "multi rename tool" might prove to be quite handy.

To tell the truth, I do use Total Commander on Ubuntu (on Wine v1.2.3). :-\"

Installing Wine plus a Windows file manager in order to rename files on Linux, this may not be to your liking.

So I wonder whether a genuine Linux file-manager which offers a lot of the functions that its Windows competitors offer, too, [**Krusader**]("http://www.krusader.org/"), will be able to do the job. At least its homepages mentions "Powerful batch renaming" as a Krusader feature.

Krusader can be found inside the Ubuntu repositories. I.e. you should be able to install it with the help of Synaptic or Software Centre, depending which of the two is available on your Ubuntu version.

Kind regards,
Karl

---

### Post by HiImTye on 2012-03-18
TBH I might consider it, doing some Google searches yield results that having the ability to rename multiple files in nautilus is a polarizing issue, with elitists spewing about CLI tools that have no -R functionality or GUI tools that might as well be CLI tools - such as gprename, which actually seems less worthy than prename, which requires the command line

I never thought that simple functionality would be such a religious issue

---

### Post by Karlchen on 2012-03-19
Hello, HiImTye.

About **Krusader** and its "powerful batch rename" capability:

When I wrote in my previous post that **Krusader** might be able to do what I could do in Total Commander by using "branchview mode" and then calling the built-in "multirename tool" or by "applying a search result" and then calling the built-in "multirename tool" on the applied list, I had not actually checked out whether the same way would work in Krusader as well. :redface:

Now when I tried, I found out that **Krusader** can indeed "apply a search result" and display all found objects in a flat list and then apply "Multirenaming" on the list.
Yet, in order to perform this multirename operation you must have installed an external programme called **[KRename]("http://www.krename.net")** first. **KRename** is available inside the Ubuntu repositories, too, just like **Krusader**.

I.e. to achieve your goal using **Krusader**, you will have to install **Krusader** plus **KRename** first.

Next you would perform a search for the files which you want to rename based on their filename extensions e.g. You feed the search result to a virtual filepanel. You mark all objects in the new filepanel and launch File => Multirename on the marked filenames.

Cannot give more details at the moment, because I have not installed **KRename**, yet. But I will in order to find out how well it performs compared to the Multirename Tool built-in to Total Commander. :-k ... A first look at **KRename** inside **Krusader** seems to suggest that **KRename** might be at least as powerful as the Total Commander Multirename functionality. 

Cheers,
Karl
--
[B][U]Beware:
[/U][/B]What I wrote about KRename is true on Ubuntu 10.04.4 32-bit e.g. This is where I tried it out.
In case you are on **Ubuntu 11.10**, however, currently the repositories will give you a faulty KRename v4.0.7-1. This is known to simply crash and do nothing. Cf. [Launchpad bug 849882]("https://bugs.launchpad.net/ubuntu/+source/krename/+bug/849882"). You might download and install **[KRename v4.0.9-1]("https://launchpadlibrarian.net/97323558/krename_4.0.9-1%7Eoneiric1%7Eppa1_i386.deb")** (backported from Pengolin) It seems to work fine on Ubuntu 11.10 and Mint12.

---

### Post by HiImTye on 2012-04-16
after thinking about it, I used the following command:
```
tye@T:~/Music$ find . -type f | grep -v -e .[mM][pP]3 -e .[jJ][pP][gG] | rename -n 's/$/.mp3/'
```obviously, I replaced -n with -v once I was sure the output was correct
also, you should change the '.' to your main Music folder, if you're not already in it so it would appear like so:
```
tye@T:~$ find ~/Music -type f | grep -v -e .[mM][pP]3 -e .[jJ][pP][gG] | rename -n 's/$/.mp3/'
```

after thinking about it again, I suppose I could have used something like this, also:
```
tye@T:~$ find ~/Music -type f | grep -v .[a-zA-Z]\{1,4\}$ | rename -n 's/$/.mp3/'
```

---

