---
title: "How do I install adobe reader with extension included for firefox in Karmic?"
date: 2009-10-31
forum: General Help
---

### Post by bhishan on 2009-10-31
How do I install adobe reader with extension included for firefox in Karmic?

---

### Post by Giblet5 on 2009-10-31
[www.adobe.com](www.adobe.com)

"Get Adobe Reader"

---

### Post by bhishan on 2009-10-31
> **Giblet5 said:**
> [www.adobe.com](www.adobe.com)

"Get Adobe Reader"

I installed the Adobe Reader from the website but it doesnot install any plugins in firefox.

---

### Post by 55tptag on 2009-10-31
Use Synaptic Package Manager and install "acroread".

---

### Post by bhishan on 2009-10-31
> **55tptag said:**
> Use Synaptic Package Manager and install "acroread".

there is no acroread in synaptic package manager. do i have to install any repository?

---

### Post by 55tptag on 2009-10-31
I don't know which repo acroread is in.

Here are my settings.  In Synaptic click "Settings->Repositories".  For the tab labeled "Ubuntu Software" I have the following checked:
- main
- universe
- restricted
- multiverse

For the tab, "Other Software" I have the following checked:
- [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

I don't think you need the medibuntu repository anymore for acroread but I'm not sure.  But, here's the link:
- [http://www.medibuntu.org/](http://www.medibuntu.org/)

When you have all of that checked then don't forget to click "Reload" in the Synaptic Package Manager prior to doing a search for acroread.

---

### Post by XCan on 2009-10-31
I believe it should be in the partner repositories.

---

### Post by bhishan on 2009-10-31
> **55tptag said:**
> I don't know which repo acroread is in.

Here are my settings.  In Synaptic click "Settings->Repositories".  For the tab labeled "Ubuntu Software" I have the following checked:
- main
- universe
- restricted
- multiverse

For the tab, "Other Software" I have the following checked:
- [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

I don't think you need the medibuntu repository anymore for acroread but I'm not sure.  But, here's the link:
- [http://www.medibuntu.org/](http://www.medibuntu.org/)

When you have all of that checked then don't forget to click "Reload" in the Synaptic Package Manager prior to doing a search for acroread.

Thanks. I dont know why but the - [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner    was not checked. I checked it, reloaded the synaptic manager and then I could find acroread in the list.:)

---

