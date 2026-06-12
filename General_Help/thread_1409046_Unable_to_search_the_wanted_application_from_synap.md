---
title: "Unable to search the wanted application from synaptic after install vmware-tools"
date: 2010-02-17
forum: General Help
---

### Post by irvinehooi on 2010-02-17
Hi, I'm running Ubuntu 9.04 (jaunty) on VMware. I found out that after installing the vmware-tools, the search result from the synaptic package manager is not accurate.

**Example:** Before I install vmware-tools, I can type **"wine"** (without the quote) in the search bar and it will display wine at the right hand side for the result.  But after successfully installed the vmware-tools, when I type **"wine"** (without the quote) it will not display any result. At first I was shocked and think that there is no such application, but when I select** "All"** section and scroll through manually I found **"wine" **is in there.

Some of the application displayed correctly like when I type **"chkconfig"** (without the quote).

May I know how to fix this problem ??

Thank you very much in advance.

---

### Post by dcstar on 2010-02-18
> **irvinehooi said:**
> Hi, I'm running Ubuntu 9.04 (jaunty) on VMware. I found out that after installing the vmware-tools, the search result from the synaptic package manager is not accurate.

**Example:** Before I install vmware-tools, I can type **"wine"** (without the quote) in the search bar and it will display wine at the right hand side for the result.  But after successfully installed the vmware-tools, when I type **"wine"** (without the quote) it will not display any result. At first I was shocked and think that there is no such application, but when I select** "All"** section and scroll through manually I found **"wine" **is in there.

Some of the application displayed correctly like when I type **"chkconfig"** (without the quote).

May I know how to fix this problem ??

Thank you very much in advance.

Ask VM questions in the Virtualization forum.

---

### Post by irvinehooi on 2010-02-18
Ops!! I manage to solve the problem. The problem happen is due to I didn't  enable the **"Third-party software"** repository from the Synaptic Package  Manager. After I enable the **"Third-party software"** repository, the  problem solved.

---

