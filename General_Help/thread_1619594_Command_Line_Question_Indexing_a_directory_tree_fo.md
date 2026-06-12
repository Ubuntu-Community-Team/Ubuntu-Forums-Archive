---
title: "Command Line Question: Indexing a directory tree for better note-taking"
date: 2010-11-12
forum: General Help
---

### Post by jon.reeve on 2010-11-12
So I have a ~/Notes directory where I keep all my notes as text files, organized into many levels of sub-directories. I use vim to view and edit them. 

I read [this post]("http://lifehacker.com/5592047/turn-your-command-line-into-a-fast-and-simple-note+taking-tool") which suggests putting this in your .bashrc: 

```

n() {
        $EDITOR ~/notes/"$*".txt
}

nls() {
        ls -c ~/notes/ | grep "$*"
}
```

Which is great, because then I'd only have to type "n vocab" to get my vocabulary list. The problem is, maybe my vocab.txt file is not in ~/Notes, but in ~/Notes/Personal/Vocab/vocab.txt. How do I get this bashrc script to index all the files in ~/Notes for easy access? 

Thanks!

---

