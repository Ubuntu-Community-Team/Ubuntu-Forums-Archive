---
title: "sed: searching single and double quote chars in text string"
date: 2010-10-27
forum: General Help
---

### Post by thaitang on 2010-10-27
I need sed to be able to search a string that includes both single quotes (') and double quotes ("). can anyone help me out, there has to be a way to do this.

So far I have tried:

sed -i '\['"]\'
sed -i '\[\'"]\'
sed -i '\[\\'"]'

 but none of these work and I cannot think of how else to escape the sed quote inside of brackets.

any ideas or solutions would be appreciated.

thanx
tt

---

### Post by dcstar on 2010-10-28
> **thaitang said:**
> I need sed to be able to search a string that includes both single quotes (') and double quotes ("). can anyone help me out, there has to be a way to do this.

So far I have tried:

sed -i '\['"]\'
sed -i '\[\'"]\'
sed -i '\[\\'"]'

 but none of these work and I cannot think of how else to escape the sed quote inside of brackets.

any ideas or solutions would be appreciated.

thanx
tt

[http://sed.sourceforge.net/sedfaq4.html](http://sed.sourceforge.net/sedfaq4.html)
4.32

---

### Post by thaitang on 2010-11-09
Hi,

Thanks for the heads up on the FAQ, but I do not see anywhere that it deals with how to search for both single and double quotes within a range enclosed by (square) brackets.

For now I am just converting all of the double quotes to another string and searching them out that way and converting them after I am completed making changes to documents, but what a PITA and I cannot imagine this is how sed was designed to do this sort of search.

Any more ideas of links to try I am eager and willing to find a solution for this, b/c I edit a lot of university text and this would help streamline things a lot for me.

cheers,
tt

---

### Post by Jacobian on 2011-08-18
I agree that this is a PITA. However, here is a workaround:

Invalid:```
sed 's|[']|\&amp;|g' file.txt
```
Valid:```
sed 's|['\'']|\&amp;|g' file.txt
```

In the second version, I've replaced the single quote with '\''. This splits the string into three pieces, which together are interpreted correctly by sed.

The second form allows you to use both single and double quotes as characters in a regular expression with sed.

---

