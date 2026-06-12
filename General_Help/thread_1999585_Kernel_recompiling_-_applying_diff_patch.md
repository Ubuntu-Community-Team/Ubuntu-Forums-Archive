---
title: "Kernel recompiling - applying diff patch"
date: 2012-06-08
forum: General Help
---

### Post by Fraoch on 2012-06-08
A rather scary request from the Linux kernel developers regarding a bug I filed...They'd like me to recompile a kernel using a patch supplied as a diff.

Now I have tried running the latest mainline kernel following these directions:

[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

which actually turned out to be a breeze, I was able to boot into the new kernel and uninstall it after testing, no problems whatsoever.  However installing a patch into a kernel is different.  The patch consists of something like the following:

"list e-mail commentary

drivers/usb/host/xhci-mem.c  |    7 ++
 drivers/usb/host/xhci-ring.c |  230 ++++++++++++++++++++++++++++++++++++++++++
 drivers/usb/host/xhci.c      |   12 ++-
 drivers/usb/host/xhci.h      |   17 +++
 4 files changed, 263 insertions(+), 3 deletions(-)

diff --git a/drivers/usb/host/xhci-mem.c b/drivers/usb/host/xhci-mem.c
index 383fc85..a842846 100644
--- a/drivers/usb/host/xhci-mem.c
+++ b/drivers/usb/host/xhci-mem.c
@@ -1685,6 +1685,7 @@ void xhci_mem_cleanup(struct xhci_hcd *xhci)
 {
 	struct pci_dev	*pdev = to_pci_dev(xhci_to_hcd(xhci)->self.controller);
 	struct dev_info	*dev_info, *next;
+	struct xhci_cd	*cur_cd, *next_cd;
 	unsigned long	flags;
 	int size;
 	int i;" etc.

so it's not in the form of patch.gz.

It looks like I'd need to apt-get source the mainline kernel, then apply the patch which would impact drivers/usb/host/xhci-mem.c in the source file tree, then build a kernel .deb, then install it.

I see bits of this on the web but nothing identical to this entire set of tasks, beginning to end.  I don't see anything about building a kernel install .deb and I'm worried it may not be as "isolated" as the method explained in the wiki - that I couldn't remove it later if something goes wrong.

Any tips?

---

