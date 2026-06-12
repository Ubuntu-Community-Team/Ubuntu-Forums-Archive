---
title: "Automatic allow &quot;Akonadi Resource&quot; to access &quot;kdewallet&quot;"
date: 2011-05-20
forum: General Help
---

### Post by vlc on 2011-05-20
Hi *,

I'm just trying to get rid of an annoying KDE Wallet dialog: Eveyting I log in I must unlock my wallet for Akonadi:

[INDENT][I]KDE Wallet Service

The application 'Akonadi Resource' has requested to open the wallet 'kdewallet'.[/I][/INDENT]

I already added Akonadi to the list of automatically allowed applications in *kwalletrc*:

[INDENT][Auto Allow]
kdewallet=Akonadi Resource,KDE Wallet Manager,Kontact,kwalletmanager

[Auto Deny]
kdewallet=

[Wallet]
Launch Manager=true
Leave Manager Open=true
Prompt on Open=false[/INDENT]

But the dialog is always displayed.

Does anyone know if there is a way to automatically grant access for Akonadi to kdewallet?

Thanks a lot in advance!

---

