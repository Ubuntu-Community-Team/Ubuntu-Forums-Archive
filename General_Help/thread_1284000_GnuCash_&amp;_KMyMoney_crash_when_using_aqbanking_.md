---
title: "GnuCash &amp; KMyMoney crash when using aqbanking for HBCI"
date: 2009-10-06
forum: General Help
---

### Post by fluse on 2009-10-06
Hello Ubuntu-Community,
 I installed GnuCash and KMyMoney and created a new user for HBCI! Everything worked perfect: I filled in the personal information and downloaded a certificate from the server of my bank. But every time when I connected to the server to do stuff like transfer money, the aqbanking-manager (which GnuCash and KMyMoney use) crashed. Here is the error message:


 Anwendung: KMyMoney (kmymoney2), Signal SIGSEGV
0x00007fc9637efcf0 in nanosleep () from /lib/libc.so.6
 Thread 1 (Thread 0x7fc96733a750 (LWP 3620)):
[KCrash Handler]
#5  0x00007fc9637c8c60 in strlen () from /lib/libc.so.6
#6  0x00007fc95bc199ac in GWEN_Text__cmpSegment (w=0x0, wpos=0x7fff6f350da0, p=0x3adb7b0 "12030000", ppos=0x0, sensecase=-16843009, matches=0x7fff6f350d9c) at text.c:1054
#7  0x00007fc95bc19c17 in GWEN_Text_ComparePattern (w=0x0, p=0x3adb7b0 "12030000", sensecase=0) at text.c:1139
#8  0x00007fc95be9d622 in AB_Banking_FindAccount () from /usr/lib/libaqbanking.so.20
#9  0x00007fc959d7ae1d in ?? () from /usr/lib/libaqhbci.so.13
#10 0x00007fc959d7bf94 in ?? () from /usr/lib/libaqhbci.so.13
#11 0x00007fc959d7c10c in ?? () from /usr/lib/libaqhbci.so.13
#12 0x00007fc959da1a2b in AH_Provider_GetSysId () from /usr/lib/libaqhbci.so.13
#13 0x00007fc9598c5ec5 in ActionGetSysId::slotButtonClicked () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#14 0x00007fc9598c604d in ActionGetSysId::qt_invoke () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#15 0x00007fc9645dbe3f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0x00007fc9645de162 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0x00007fc964610706 in QWidget::event () from /usr/lib/libqt-mt.so.3
#18 0x00007fc96457e4a5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#19 0x00007fc96457f497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#20 0x00007fc9651043f2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#21 0x00007fc96451cffc in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#22 0x00007fc96451bc4e in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#23 0x00007fc96452e82a in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#24 0x00007fc964594ec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#25 0x00007fc96474c650 in QDialog::exec () from /usr/lib/libqt-mt.so.3
#26 0x00007fc9598c7416 in WizardPinTanNew::exec () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#27 0x00007fc9598b28c6 in UserWizard::_handleModePinTan () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#28 0x00007fc9598b3528 in UserWizard::exec () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#29 0x00007fc9598ae928 in CfgModuleHbci::createNewUser () from /usr/lib/aqbanking/plugins/20/frontends/qbanking/cfgmodules/aqhbci.so
#30 0x00007fc95c14e923 in ?? () from /usr/lib/libqbanking.so.5
#31 0x00007fc95c14f475 in ?? () from /usr/lib/libqbanking.so.5
#32 0x00007fc9645dbe3f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#33 0x00007fc9645de162 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#34 0x00007fc964610706 in QWidget::event () from /usr/lib/libqt-mt.so.3
#35 0x00007fc96457e4a5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#36 0x00007fc96457f497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#37 0x00007fc9651043f2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#38 0x00007fc96451cffc in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#39 0x00007fc96451bc4e in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#40 0x00007fc96452e82a in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#41 0x00007fc964594ec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#42 0x00007fc96474c650 in QDialog::exec () from /usr/lib/libqt-mt.so.3
#43 0x00007fc95c135934 in QBCfgTab::exec () from /usr/lib/libqbanking.so.5
#44 0x00007fc95c3b69b0 in KBankingPlugin::slotSettings () from /usr/lib/kde3/kmm_kbanking.so
#45 0x00007fc95c3b8d11 in KBankingPlugin::qt_invoke () from /usr/lib/kde3/kmm_kbanking.so
#46 0x00007fc9645dbe3f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#47 0x00007fc9645de162 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#48 0x00007fc965679df0 in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#49 0x00007fc96567a0f8 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#50 0x00007fc9645dbe3f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#51 0x00007fc9648eda8d in QSignal::signal () from /usr/lib/libqt-mt.so.3
#52 0x00007fc9645f59e4 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#53 0x00007fc9646d666d in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#54 0x00007fc964610706 in QWidget::event () from /usr/lib/libqt-mt.so.3
#55 0x00007fc96457e4a5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#56 0x00007fc96457f497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#57 0x00007fc9651043f2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#58 0x00007fc96451d271 in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#59 0x00007fc96451bc4e in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#60 0x00007fc96452e82a in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#61 0x00007fc964594ec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#62 0x00007fc964594d82 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#63 0x000000000056cd65 in main ()

---

### Post by Hei Ku on 2009-10-08
Did you solve this? How did you install the applications? Where did you install them from?

---

### Post by fluse on 2009-10-10
No. I isn't solved jet.
I installed the application with the application-manager. I just selected it and pressed install :)

Hope you can help me!

Greetings,
fluse

---

### Post by Hei Ku on 2009-10-10
Did you start the aqbanking-manager from inside KMyMoney? 
As far as I knew, the Ubuntu version did not have the aqbanking plugins enabled. 

Also, did you install those plugins or only aqbanking and kmymoney? They are in a kmymoney-plugins package or something like that.

---

### Post by fluse on 2009-10-16
Yes, I start the aqbanking-manager from inside KMyMoney!

I installed kmymoney-plugins and kmymoney...

Greetings,
Fluse

---

### Post by Hei Ku on 2009-10-16
What version of aqbanking are you using? Not all versions are compatible with KMyMoney.

---

