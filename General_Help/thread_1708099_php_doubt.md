---
title: "php doubt"
date: 2011-03-16
forum: General Help
---

### Post by rahulbest on 2011-03-16
i want to make help button such that when some one clicks it he should get help....
the help details r stored in that php file only but made invisible...but on clicking it should be visible.
plz tell me how to make this thing invisible and visible in php?
thanks in advance

---

### Post by satish_j on 2011-03-16
You need to use Javascript to achieve this.On first click on link,it will be visible..on second click,it be made invisible i.e sort of toggle...

---

### Post by rahulbest on 2011-03-16
php and java script used in one web page doesnt cause prob???

---

### Post by satish_j on 2011-03-16
> **rahulbest said:**
> php and java script used in one web page doesnt cause prob???

Not at all,in fact most pages on web uses a combination of these two,as the power of these two is what makes the web pages more attractive!!!

---

### Post by pqwoerituytrueiwoq on 2011-03-16
The best way would be to use CSS JS
If you notice the JS is in the onclick attribute
HTML-->
```
<span class="hide" onclick="this.className=this.className=='hide'?'show':'hide'">I am a help topic<p class="help">I am a help message</p></span>
```CSS-->
```
.hide .help{
    display:none;
}
.show .help{
    display:inline;
}
```

Edit:
@[satish_j]("http://ubuntuforums.org/member.php?u=779331")
1st link in your sig needs instructions for grub2

---

### Post by rahulbest on 2011-03-27
thnks guys..:)

---

