---
title: "Interesting Kernel Behavior"
date: 2011-10-10
forum: General Help
---

### Post by sjohnston on 2011-10-10
Hi Everyone,

I an seeing an interesting kernel issue.  I am trying to configure the 2.6.38.8 kernel to have Intel Trusted Execution Technology (TXT) support, here are my results:

Using Ubuntu 11.04 - I am able to see the option for the Intel TXT Security options.

Using Ubuntu 10.04 - I am not able to see the option for Intel TXT and doing a search in menuconfig for "TXT" returns [=n] for HAVE_INTEL_TXT.  Even though the return is [=y] in Ubuntu 11.04 and I know I have TXT (it is activated in the BIOS along with TPM, VT-x, and VT-d) I am not able to configure the option.

I am using a Dell E6510 with A09 BIOS and TPM v1.2.  The kernel is 2.6.38.8.  Screenshots of the kernel configs are attached.

Has anyone else seen this issue?  


Steve

---

### Post by sjohnston on 2011-10-12
Found the solution:

The "Enable Intel(R) Trusted Execution Technology (Intel(R)
TXT)" does not actually appear by default.

After recursively grepping Kconfig files, I found that HAVE_INTEL_TXT
is defined in
arch/x86/Kconfig:

config HAVE_INTEL_TXT
        def_bool y
        depends on EXPERIMENTAL && DMAR && ACPI

...however the search result page (i.e., using "/" in `make
menuconfig`) does not show these dependencies.  The search result page
for CONFIG_DMAR does suggest that CONFIG_PCI_MSI is necessary, and
after enabling CONFIG_PCI_MSI, CONFIG_DMAR becomes available, and
after enabling that, then CONFIG_INTEL_TXT becomes available back in
the Security Options menu.

---

