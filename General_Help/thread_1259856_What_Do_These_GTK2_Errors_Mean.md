---
title: "What Do These GTK2 Errors Mean?"
date: 2009-09-06
forum: General Help
---

### Post by LaneLester on 2009-09-06
I have a weather station program that used to run with the QT libraries. The developer switched to GTK2, and although others are not having a problem, these are the errors I get:
```
GLib-CRITICAL **: file gmessages.c: line 293 (g_log_remove_handler): assertion `handler_id > 0' failed.
[FORMS.PP] ExceptionOccurred 
  Sender=EAccessViolation
  Exception=Access violation
  Stack trace:
  $00821A80
  $00BBF9F7
  $00BBFAAD
  $0056D63E
  $0056D674
  $08AC1A6A  TGTKWIDGETSET__PASSCMDLINEOPTIONS,  line 293 of gtkwidgetset.inc
  $08AC192B  TGTKWIDGETSET__CREATE,  line 213 of gtkwidgetset.inc
  $0808D3AC  CREATEWIDGETSET,  line 1590 of forms.pp
  $0808CB1D  INTERFACES_init,  of gtk1int.pp
  $08C662C4
TApplication.HandleException Access violation
  Stack trace:
  $00821A80
  $00BBF9F7
  $00BBFAAD
  $0056D63E
  $0056D674
  $08AC1A6A  TGTKWIDGETSET__PASSCMDLINEOPTIONS,  line 293 of gtkwidgetset.inc
  $08AC192B  TGTKWIDGETSET__CREATE,  line 213 of gtkwidgetset.inc
  $0808D3AC  CREATEWIDGETSET,  line 1590 of forms.pp
  $0808CB1D  INTERFACES_init,  of gtk1int.pp
  $08C662C4
[FORMS.PP] ExceptionOccurred 
```

Can you tell what's wrong? And even better, how to fix it?

Lane

---

