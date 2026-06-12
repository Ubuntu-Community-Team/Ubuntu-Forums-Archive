---
title: "create a tar file from a file list"
date: 2010-08-18
forum: General Help
---

### Post by wblogan on 2010-08-18
To create a tar archive of the dot files in my /home directory. I did ```
find ./ -name ".*" > dotfiles
``` and then ```
tar -czvf <filename>.tar.gz --files-from ./dotfiles
```. I also tried ```
tar -czvf <filename>.tar.gz -T ./dotfiles
``` So I tried several other things, none of which worked. I can find nothing on the web. I can get it done using the exclude option, but I'd still like to know if a tar file can be created from a file containing a list of files, and if so how.

TIA

---

### Post by Zorgoth on 2010-08-18
find -name '.*' finds enverything on account of the working directory being .

Try

```

find -regex '\./\.[^/]*' -exec tar -rf newarchive.tar {} \;

```

The regular expression says the following:

Match files in the current directory (./) whose names begin with a . (. has a special meaning in regular expressions so it is escaped with a backslash) followed by any combination of characters NOT containing a / - thus, for example, you will get ./.local but not ./.local/share and all the other stuff inside it you don't want to append after it has already been added by appending .local.

Note that this will not find hidden files inside non-hidden directories in your home directory, but I doubt you want those - I could get them but I think you don't want them if they exist.

tar -rf just appends its argument to the end of a tar archive, allowing you to use find -regex -exec as your tool (since find -regex -exec has to work one command at a time).

Read man grep for an explanation of regular expressions.

---

### Post by wblogan on 2010-08-18
Thanks for the reply Zorgoth. I'll try your suggestion. I can see that my post was a bit unclear. I got the files I wanted into "dotfiles" using the find command. What I'm wondering is why I can't use "dotfiles" to create the tar.

---

### Post by Zorgoth on 2010-08-18
Well, the first thing to note is that find '.*' is definitely not going to work, as I already said; it will find every single file in your home directory.  You can try using my find -regex with > instead of -exec to test your dotfile when you have the right directory names.

---

### Post by Zorgoth on 2010-08-18
I have confirmed that creating dotfile as follows:

find -regex '\./\.[^/]*' > ./dotfile

and executing tar as follows:

tar -cvnf archive.tar -T dotfile

works just fine.

The problem was probably that your

find -name '.*'

created crazy contradictions and weirdnesses.

---

### Post by wblogan on 2010-08-18
You're right. I overlooked that the first entry in my dotfile was "./". I confirmed as well that your code works. Thanks again. You saved me a few of the hairs that I have left.

---

