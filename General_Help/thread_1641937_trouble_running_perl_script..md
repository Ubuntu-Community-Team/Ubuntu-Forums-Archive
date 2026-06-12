---
title: "trouble running perl script."
date: 2010-12-09
forum: General Help
---

### Post by owners4life5 on 2010-12-09
hello,

i am trying to find a screensaver for my terminal, right, and i finally find one called 'asciiquarium'. [http://www.robobunny.com/projects/asciiquarium/html/](http://www.robobunny.com/projects/asciiquarium/html/)
anyway, it looks interesting and all, i have marked the file as executable and everything, but when i go to run it, i get this:

```
brian@brian-COMPAQ-Presario-SR1103WM:~/Downloads/asciiquarium_1.0$ ./asciiquarium
Can't locate Term/Animation.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./asciiquarium line 42.
BEGIN failed--compilation aborted at ./asciiquarium line 42.
brian@brian-COMPAQ-Presario-SR1103WM:~/Downloads/asciiquarium_1.0$ 

```

what can i do for this??? i would really like to have that screensaver..

---

### Post by bhaverkamp on 2010-12-09
Use cpan to install Term::Animation. There is an option to setup the CPAN installers to chase down dependencies. I forget the details on that; otherwise you may need to run CPAN more than once to handle the other missing libraries.

---

### Post by wojox on 2010-12-09
[http://www.robobunny.com/projects/asciiquarium/README](http://www.robobunny.com/projects/asciiquarium/README)

---

### Post by sisco311 on 2010-12-09
> **wojox said:**
> [http://www.robobunny.com/projects/asciiquarium/README](http://www.robobunny.com/projects/asciiquarium/README)

+1

@OP:

You have to install libcurses-perl and the [Term::Animation]("http://search.cpan.org/~kbaucom/Term-Animation-2.4/lib/Term/Animation.pm") module.

---

### Post by owners4life5 on 2010-12-09
> **bhaverkamp said:**
> Use cpan to install Term::Animation. There is an option to setup the CPAN installers to chase down dependencies. I forget the details on that; otherwise you may need to run CPAN more than once to handle the other missing libraries.

i don.t have very much experience with perl, so how exactly do i go about doing this?

---

### Post by sisco311 on 2010-12-09
> **owners4life5 said:**
> i don.t have very much experience with perl, so how exactly do i go about doing this?

You download the module from the link I posted. Extract it and read the README file for installation instructions. You have to run **make install** as root (**sudo make install**).

---

### Post by owners4life5 on 2010-12-09
> **sisco311 said:**
> +1

@OP:

***_You have to install libcurses-perl_*** and the [Term::Animation]("http://search.cpan.org/~kbaucom/Term-Animation-2.4/lib/Term/Animation.pm") module.

that did it.

attached is a screenshot of it working. thank you guys very much. marking as solved.

---

### Post by sisco311 on 2010-12-09
Cool!  You're welcome.

---

