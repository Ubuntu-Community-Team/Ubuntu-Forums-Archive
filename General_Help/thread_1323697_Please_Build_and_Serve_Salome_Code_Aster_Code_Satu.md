---
title: "Please Build and Serve: Salome Code_Aster Code_Saturne CFD CAE FEA FEM"
date: 2009-11-11
forum: General Help
---

### Post by BrendaEM on 2009-11-11
[B]Experienced at building/compiling?
Want a challenge?
Looking to build software that would cost $7000-$14,000 on the free market?[/B]

Hi,

It would be a great help to experimenters, researchers, and educators if these programs were made available for apt-get. They comprise not only a powerful FEA/FEM/CFD suite, but also a Open-Source "power-application," and another reason to choose Ubuntu, should this be easy to install.

The main issue is: the myriad of depends they require, I feel are out of the skill level for the average user/installer, but would not packaging them for apt-get solve this?

Salome can also be set up to encapsulate the others. There is some work under way in Debian, but I don't know where it stands. There is the CAELinux suite, but I feel that maintaining an entire distro means that the core software update cycle suffers.

If you are an experience building, please give it a try. A 64-bit versions would be most helpful, as the software is demanding on resources to run.

*Thank you for your consideration.*

Code_Saturne CFD
[http://research.edf.com/the-edf-offers/research-and-development/softwares/code-saturne/code-saturne-download-107009.html](http://research.edf.com/the-edf-offers/research-and-development/softwares/code-saturne/code-saturne-download-107009.html)

Salome Pre/Post
[http://www.salome-platform.org/](http://www.salome-platform.org/)

Code_Aster
[http://www.code-aster.org/V2/spip.php?rubrique21](http://www.code-aster.org/V2/spip.php?rubrique21)

I've also posted a thread on the Salome forums.
[http://www.salome-platform.org/forum/forum_9/504522496](http://www.salome-platform.org/forum/forum_9/504522496)

---

### Post by Takala on 2009-11-21
> **BrendaEM said:**
> [B]Experienced at building/compiling?
Want a challenge?
Looking to build software that would cost $7000-$14,000 on the free market?[/B]

Hi,

It would be a great help to experimenters, researchers, and educators if these programs were made available for apt-get. They comprise not only a powerful FEA/FEM/CFD suite, but also a Open-Source "power-application," and another reason to choose Ubuntu, should this be easy to install.

The main issue is: the myriad of depends they require, I feel are out of the skill level for the average user/installer, but would not packaging them for apt-get solve this?

Salome can also be set up to encapsulate the others. There is some work under way in Debian, but I don't know where it stands. There is the CAELinux suite, but I feel that maintaining an entire distro means that the core software update cycle suffers.

If you are an experience building, please give it a try. A 64-bit versions would be most helpful, as the software is demanding on resources to run.

*Thank you for your consideration.*

Code_Saturne CFD
[http://research.edf.com/the-edf-offers/research-and-development/softwares/code-saturne/code-saturne-download-107009.html](http://research.edf.com/the-edf-offers/research-and-development/softwares/code-saturne/code-saturne-download-107009.html)

Salome Pre/Post
[http://www.salome-platform.org/](http://www.salome-platform.org/)

Code_Aster
[http://www.code-aster.org/V2/spip.php?rubrique21](http://www.code-aster.org/V2/spip.php?rubrique21)

I've also posted a thread on the Salome forums.
[http://www.salome-platform.org/forum/forum_9/504522496](http://www.salome-platform.org/forum/forum_9/504522496)

Hi Brenda,

If I remember correctly,  there has been some issues with the licences. Adam Powel from Opennovation has done a lot of great work in order to put these cad/engineering packages together:
[http://www.opennovation.org/ubuntu/](http://www.opennovation.org/ubuntu/)

From there you can see that the for example opencascade library which salome is using, is allready at the repositories. However, I've read somewhere, that the whole salome might never be part of debian or ubuntu because of the licence issues...

By the way. Is there something particular that you need to do with those applications you mentioned. For multiphysical modelling for example, you could give "Elmer" a try, it is a very nice tool, I recommend it. Check out [www.elmerfem.org]("http://www.elmerfem.org"). Elmer doesn't include cad for drawing but it is able to mesh.

---

### Post by BrendaEM on 2009-11-27
Actually, I have three or four projects planned/hoped to do.

For Linux, Ubuntu 8.04 is old, for a desktop user, it very old to use. I thought that the Salome/Saturne/Aster/OpenCascade license issues were sorted out, and it was starting to be built for Debian. If that is not true, perhaps they should be called on it...again.

I've not seen many 3D CFD and FE examples in Elmer, but I will check into it again. I've seen imcompressable flow, but that's not going to help me for what I',m working on.

Still, one of these things could be ported to GTK2, with the emphasis on it working with a major distribution.

Generally the GUIs and workflow, of science applications could be improved. Installing and maintaining most of these programs goes beyond what the average Linux user would want to do, or capable of. So much promise.... : (

---

