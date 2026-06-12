---
title: "How to download as root"
date: 2009-12-14
forum: General Help
---

### Post by glavkos on 2009-12-14
How to download a file as a root ...So the file goes to the root directory and not to the /home/user/etc...

                   Grateful in advance for your help

---

### Post by synapsys on 2009-12-14
I suppose you could use wget to do this. What file are you downloading and why does it need to go directly to the root directory?

---

### Post by benj1 on 2009-12-14
log in as root, which isn't recommended, or sudo downloadmanager/webbrowser, what are you trying to achieve?

---

### Post by Chesamo on 2009-12-14
What file could you possibly be downloading that would need to go into /root?

---

### Post by baddog144 on 2009-12-14
You could just cd to the /root directory (in a terminal), and:
```

sudo wget http://this.com/thatfile.foo

```

---

### Post by Joshua on 2009-12-14
Not sure what software you are using to download, but you could try sudo -H [program] or gksudo -H [program].

I think the "-H" sets the home directory to that of the target user - which should be root.

---

### Post by bathmateus363 on 2009-12-14
You have just found the only safe, proven and permanent natural remedies for impotence & erectile dysfunction with a 100% money-back guarantee.

Erectile Dysfunction affects most men at some time in their lives, and for some it is more than just a temporary problem. Bathmate helps with these problems, and improves the lives of virtually all who use it.  Remember that you want natural remedies for impotence & erectile dysfunction.  The Bathmate hydropump provides this!

Doctors have prescribed (and even designed) pumps for erectile dysfunction for many years.  But are they natural remedies for impotence & erectile dysfunction? The Bathmate hydropump, designed by engineers, not doctors, is the first and only ump that uses water, termed hydropump. The innovation of water for penis pumps makes for supreme efficiency and safety. The Bathmate mimics the effect that is achieved during a natural erection in the way that it draws blood into the penile blood vessels. The Bathmate hydropump exercises the penis and moves blood into vascular areas which may not have been able to carry as much blood before. By encouraging more blood to flow freely through these veins the Bathmate hydropump has been found to be highly beneficial to men experiencing erectile dysfunction and to provide natural remedies for impotence & erectile dysfunction.

Bathmate hydropump has been proven to have a positive effect from even the first session and when used regularly erection problems soon become a thing of the past.

The Bathmate hydropump gives every man the opportunity to achieve his greatest sexual potential!

Erectile dysfunction (ED or "male impotence") is a sexual dysfunction characterized by the inability to develop or maintain an erection of the penis sufficient for satisfactory sexual performance. The Bathmate hydropump by Bathmate provides the best solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are the best.

Erectile dysfunction (ED) is the inability of a man to maintain a firm erection long enough to have sex. Although erectile dysfunction is more common in older men, this common problem can occur at any age. Having trouble maintaining an erection from time to time isn't necessarily a cause for concern. But if the problem is ongoing, it can cause stress and relationship problems and affect self-esteem. The Bathmate hydropump by Bathmate provides the most comprehensive and complete solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are the are safe.

An erection occurs as a hydraulic effect due to blood entering and being retained in sponge-like bodies within the penis. The process is most often initiated as a result of sexual arousal, when signals are transmitted from the brain to nerves in the pelvis. Erectile dysfunction is indicated when an erection is consistently difficult or impossible to produce, despite arousal. There are various and often multiple underlying causes, some of which are treatable medical conditions. The most important organic causes are cardiovascular disease and diabetes, neurological problems (for example, trauma from prostatectomy surgery), hormonal insufficiencies (hypogonadism) and drug side effects. It is important to realize that erectile dysfunction can signal underlying risk for cardiovascular disease. The Bathmate hydropump by Bathmate provides is totally natural and safe. Natural remedies for impotence & erectile dysfunction have no side effects.


Formerly called impotence, erectile dysfunction was once a taboo subject. It was considered a psychological issue or a natural consequence of growing older. These attitudes have changed in recent years. It's now known that erectile dysfunction is more often caused by physical problems than by psychological ones, and that many men have normal erections into their 80s. The Bathmate hydropump by Bathmate provides the best solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction last the longest.

There is often a contributing and complicating and sometimes a primary psychological or relational problem. Psychological impotence is where erection or penetration fails due to thoughts or feelings (psychological reasons) rather than physical impossibility; this can often be helped. Notably in psychological impotence, there is a strong response to placebo treatment. Erectile dysfunction, tied closely as it is to cultural notions of potency, success and masculinity, can have severe psychological consequences. There is a strong culture of silence and inability to discuss the matter. In reality, it has been estimated that around 1 in 10 men will experience recurring impotence problems at some point in their lives.  The Bathmate hydropump by Bathmate is the easiest to use and safest penis pump in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are easiest to use.

Although it can be embarrassing to talk with your doctor about sexual issues, seeking help for erectile dysfunction can be worth the effort. Erectile dysfunction treatments ranging from medications to surgery can help restore sexual function for most men. Sometimes erectile dysfunction is caused by an underlying condition such as heart disease. So it's important to take erectile trouble seriously because it can be a sign of a more serious health problem.  The Bathmate hydropump by Bathmate provides the least expensive in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are lower cost.

Besides treating the underlying causes and psychological consequences, the first line treatment of erectile dysfunction consists of a trial of PDE5 inhibitor drugs (the first of which was sildenafil or Viagra). In some cases, treatment can involve prostaglandin tablets in the urethra, intracavernous injections with a fine needle into the penis that cause swelling, a penile prosthesis, a penis pump or vascular reconstructive surgery. The Bathmate hydropump by Bathmate provides the most most effective solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are the most effective.

Erectile dysfunction is the inability to maintain an erection sufficient for sexual intercourse at least 25 percent of the time. The Bathmate hydropump by Bathmate provides the least invasive and bothersome solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are less invasive.

The Latin term impotentia coeundi describes simple inability to insert the penis into the vagina. It is now mostly replaced by more precise terms. The study of erectile dysfunction within medicine is covered by andrology, a sub-field within urology. The Bathmate hydropump by Bathmate provides the most fun and enjoyable solution to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction are more fun to use.

An occasional inability to maintain an erection happens to most men and is normal. But ongoing erection problems are a sign of erectile dysfunction and should be evaluated. In some cases, erectile dysfunction is the first sign of another underlying health condition that needs treatment. The Bathmate hydropump by Bathmate provides the best results out of all penis pumping solutions to erectile dysfuntion in the USA and worldwide. Natural remedies for impotence & erectile dysfunction provide the best results.

---

### Post by doas777 on 2009-12-14
I see that bathmateus363 went and dowloaded somthing as root.
good for her. [Edit: the mods have removed a very spamilicious post, rendering my jest impotent. pun intended]

OP: I would download as a normal user and copy the file to the /root folder. you can access /root for write, by hitting Alt + F2, and entering 
```
gksu nautilus
```navigating to /root, and pasting.

---

### Post by SuperSonic4 on 2009-12-14
> **glavkos said:**
> How to download a file as a root ...So the file goes to the root directory and not to the /home/user/etc...

                   Grateful in advance for your help

I would be instantly suspicious of any program that asks you to download something as root. Do you have a link to the website?

In this case you can download the file as user and then use sudo to copy it into root's home.

---

### Post by snowpine on 2009-12-14
> **doas777 said:**
> I see that bathmateus363 went and dowloaded somthing as root.
good for her.

LOL!

Seriously, to the OP... DON'T download as root! Why on earth would you give the **Internet** root access to your computer?

Download the file to your home folder, then once the download is complete (and you've verified it's nothing malicious), copy the file to root (using the terminal or 'gksu nautilus'). That is the safe way.

---

### Post by Joshua on 2009-12-14
Some sort of root would be a little more natural that what bathmateus363 looks to be describing.

By the way, I like snowpine's solution best.

---

### Post by SuperSonic4 on 2009-12-14
> **Joshua said:**
> Some sort of root would be a little more natural that what bathmateus363 looks to be describing.

By the way, I like snowpine's solution best.

Which is the same as doas777 and mine :p

---

### Post by snowpine on 2009-12-14
> **SuperSonic4 said:**
> Which is the same as doas777 and mine :p

Yeah but I said it with more irony. :)

---

### Post by Joshua on 2009-12-14
> **SuperSonic4 said:**
> Which is the same as doas777 and mine :p

Yeah, but snowpine had such a poetic delivery - with the LOL and the **bold type**.  ;)  I just thought it funny that the last three popped up so quickly and were all the same.

edit: Shoot. I type too slow.

---

### Post by glavkos on 2009-12-15
> **synapsys said:**
> I suppose you could use wget to do this. What file are you downloading and why does it need to go directly to the root directory?

i want to download a libvl archive to fix an up-down problem in my web cam. The creator of this archive recommended to download it as root so i can to figure and install this file. 

[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz]("http://people.fedoraproject.org/%7Ejwrdegoede/libv4l-0.6.4-test.tar.gz") here is the link you asked me about...

---

### Post by 3rdalbum on 2009-12-15
Don't download it as root. Just download it as your normal user account.

Then whenever it tells you to run something as root, put the "sudo" command before it.

For instance, it will probably tell you to:

```
./configure
make
make install (as root)
```

or possibly:

```
./configure
make
su
make install
```

Instead of typing "su" and then "make install", just type "sudo make install".

You only need root to modify files outside your home directory, so the only step that requires root access is the "make install" which installs the compiled files to your system.

---

