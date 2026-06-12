---
title: "How do I add debian packages to Synaptic Package Manager?"
date: 2011-10-15
forum: General Help
---

### Post by GeoffreyBernardo on 2011-10-15
In Synaptic, when I click **File** **[B]>**[/B] **Add** **downloaded packages** and navigate to the folder with the debian packages, the debian packages are greyed out, which means I cannot select them.

---

### Post by dcstar on 2011-10-15
> **GeoffreyBernardo said:**
> In Synaptic, when I click **File** **[B]>**[/B] **Add** **downloaded packages** and navigate to the folder with the debian packages, the debian packages are greyed out, which means I cannot select them.

Doing something like that will basically guarantee that your Ubuntu system will be wrecked.

Ubuntu **is not** Debian, is is a fork of Debian.

---

### Post by mc4man on 2011-10-15
i think possibly you should expose & read the tool-tip for that option, it's not what you think it is

---

### Post by varunendra on 2011-10-17
> **GeoffreyBernardo said:**
> In Synaptic, when I click **File** **[B]>**[/B] **Add** **downloaded packages**  and navigate to the folder with the debian packages, the debian  packages are greyed out, which means I cannot select them.
Did you notice the balloon tip when you hover the mouse over that option  (Add downloaded packages)? There is another option just above it - **"Generate package download script"**.  I have never tried it (never needed to), but the balloon tip suggests  that you can only add those packages which are downloaded using that  script option above.


> **dcstar said:**
> Doing something like that will basically guarantee that your Ubuntu system will be wrecked.

Ubuntu **is not** Debian, is is a fork of Debian.
Does it mean that although the option is there, it generally 'should not be used'? Just like the release 'Upgrade' button?
I'm asking because I have manually installed many packages in the past. The only hassle was to install the dependencies in correct order (and I know it sometimes can be a perfect recipe for disaster). So I think if there is a similar option in synaptic itself, it should be intelligent enough to ensure consistency.

---

### Post by mc4man on 2011-10-17
> **varunendra said:**
> 
Does it mean that although the option is there, it generally 'should not be used'? Just like the release 'Upgrade' button?
I'm asking because I have manually installed many packages in the past. The only hassle was to install the dependencies in correct order (and I know it sometimes can be a perfect recipe for disaster). So I think if there is a similar option in synaptic itself, it should be intelligent enough to ensure consistency.
The option(s) exist only for repos that are in your sources which excluding ppa's should only be ubuntu ones

While one can install some Debian packages it's generally a very poor idea, Debian uses a different naming, just that alone can lead to issues, big or small
Adding Debian repos to one's sources is pretty much  guaranteed to bork your install sooner or later.

Whether the Op meant debian as in .deb but built for ubuntu or debian as in from Debian is maybe a bit unclear, only he/she would know..

---

