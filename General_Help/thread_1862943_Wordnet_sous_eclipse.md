---
title: "Wordnet sous eclipse"
date: 2011-10-17
forum: General Help
---

### Post by nounouuuuu2011 on 2011-10-17
Bonjour,
je veux utiliser wordnet sous Eclipse sachant que je travaille sous Ubuntu(Linux).
j'ai téléchargé le package et j'ai suivi ces instructions pour l'installation :
[http://aventurineyao.blogspot.com/2010/02/procedure-to-install-wordnet-on-ubuntu.html]("http://aventurineyao.blogspot.com/2010/02/procedure-to-install-wordnet-on-ubuntu.html")

j'ai eu un problème sous eclipse :

> Exception in thread "main" java.lang.NullPointerException
at didyoumean.TagFilter.Syntaxtic_Filtring(TagFilter.java:60)
at didyoumean.TagFilter.main(TagFilter.java:81)
voici le bout de code où réside le problème:
```
indexWord =dict.getIndexWord(((POS)POS.getAllPOS().get(h)),tag);
```
Est-ce que je dois utiliser un fichier xml. Et si oui d'où dois-je le télécharger?
Pouvez-vous m'aider?

---

