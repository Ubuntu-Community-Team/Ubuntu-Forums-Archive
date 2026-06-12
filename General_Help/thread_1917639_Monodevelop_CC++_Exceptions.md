---
title: "Monodevelop C/C++ Exceptions"
date: 2012-01-30
forum: General Help
---

### Post by zizzdude on 2012-01-30
I'm not sure why, but I get strange exceptions in Monodevelop (2.6 from the repository, Xubuntu 11.10) when writing c/c++ programs. 

When I try writing new functions,

example:
```

void example_fuction() ...

```

I get this exception:

```

System.IndexOutOfRangeException: Array index is out of range.
  at Mono.TextEditor.GapBuffer.GetCharAt (Int32 offset) [0x00000] in <filename unknown>:0 
  at Mono.TextEditor.Document.GetCharAt (Int32 offset) [0x00000] in <filename unknown>:0 
  at Mono.TextEditor.TextEditorData.GetCharAt (Int32 offset) [0x00000] in <filename unknown>:0 
  at CBinding.CTextEditorExtension.ResetTriggerOffset (MonoDevelop.Ide.CodeCompletion.CodeCompletionContext completionContext) [0x00000] in <filename unknown>:0 
  at CBinding.CTextEditorExtension.HandleCodeCompletion (MonoDevelop.Ide.CodeCompletion.CodeCompletionContext completionContext, Char completionChar, System.Int32& triggerWordLength) [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Content.CompletionTextEditorExtension.KeyPress (Key key, Char keyChar, ModifierType modifier) [0x00000] in <filename unknown>:0 
  at CBinding.CTextEditorExtension.KeyPress (Key key, Char keyChar, ModifierType modifier) [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Content.TextEditorExtension.KeyPress (Key key, Char keyChar, ModifierType modifier) [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Content.TextEditorExtension.KeyPress (Key key, Char keyChar, ModifierType modifier) [0x00000] in <filename unknown>:0 
  at MonoDevelop.SourceEditor.ExtensibleTextEditor.ExtensionKeyPress (Key key, UInt32 ch, ModifierType state) [0x00000] in <filename unknown>:0 

```

when double-clicking on a function in the "Classes" tab usually on the right panel, I get:

```

System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ArgumentException: column < MinColumn
  at Mono.TextEditor.TextEditor.SetCaretTo (Int32 line, Int32 column, Boolean highlight) [0x00000] in <filename unknown>:0 
  at Mono.TextEditor.TextEditorData.SetCaretTo (Int32 line, Int32 column, Boolean highlight) [0x00000] in <filename unknown>:0 
  at Mono.TextEditor.TextEditorData.SetCaretTo (Int32 line, Int32 column) [0x00000] in <filename unknown>:0 
  at CBinding.Navigation.LanguageItemCommandHandler.ActivateItem () [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Components.NodeCommandHandler.ActivateMultipleItems () [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Components.ExtensibleTreeView.ActivateCurrentItem () [0x00000] in <filename unknown>:0 
  at MonoDevelop.Ide.Gui.Components.ExtensibleTreeView.OnNodeActivated (System.Object sender, Gtk.RowActivatedArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (System.Reflection.MonoMethod,object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0 

```

These do not hinder me from writing programs, but I do wonder if they can be avoided. 

Is there anything I can do?

Thanks :)

---

