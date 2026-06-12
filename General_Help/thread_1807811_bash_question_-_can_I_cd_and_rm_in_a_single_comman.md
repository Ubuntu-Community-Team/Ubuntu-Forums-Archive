---
title: "bash question - can I cd and rm in a single command?"
date: 2011-07-19
forum: General Help
---

### Post by Keypel on 2011-07-19
I delete a particular file often. first I have to cd then I have to rm.Is there a way to do this on a single line?

example 

cd ./ssh rm known_hosts

that doesn't but is there a way to do it? I known, silly question.

---

### Post by blind2314 on 2011-07-19
```
cd foo; rm foo2
```

---

### Post by Keypel on 2011-07-19
So I just put the ";" after the first command?

What is this foo stuff? I never understood what foo is. lol

Anyways thanks, it worked.

---

### Post by bodhi.zazen on 2011-07-19
you do not need the cd at all

rm .ssh/known_hosts

and you do not need to delete that particular file, or at least there are better ways of managing .ssh/known_hosts 

Much better to use ssh-keygen -R host_name , See: [http://bodhizazen.net/Tutorials/SSH_overview#Security](http://bodhizazen.net/Tutorials/SSH_overview#Security)

---

### Post by Habitual on 2011-07-19
rm ~/.ssh/known_hosts seems more "efficient.

---

### Post by AlphaLexman on 2011-07-19
> **Keypel said:**
> What is this foo stuff? I never understood what foo is. lol
'foo' and 'bar' are just fake names. See [http://en.wiktionary.org/wiki/foo]("http://en.wiktionary.org/wiki/foo")

---

### Post by Keypel on 2011-07-19
Thanks for all the wonderful replies. _All_ of them were helpful.

I really have a love for this kind of stuff. I hope to become fluent one of these days.

foo bar lol hahaha I get it now.

Oh, that's hilarious. foo and bar (foobar). A Phonetic spelling of &#8220;FUBAR&#8221;, an acronym for &#8220;f#cked up beyond all recognition&#8221;.

Apparently, the Linux community has a funny sense of humor.

Oh, that's too funny!!

-

---

