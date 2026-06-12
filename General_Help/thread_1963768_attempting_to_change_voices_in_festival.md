---
title: "attempting to change voices in festival"
date: 2012-04-22
forum: General Help
---

### Post by gardengxc on 2012-04-22
I'm attempting to use Voice_ to change the default voice but,
```
Festival Speech Synthesis System 2.1:release November 2010
Copyright (C) University of Edinburgh, 1996-2010. All rights reserved.

clunits: Copyright (C) University of Edinburgh and CMU 1997-2010
hts_engine: 
The HMM-based speech synthesis system (HTS)
hts_engine API version 1.04 (http://hts-engine.sourceforge.net/)
Copyright (C) 2001-2010  Nagoya Institute of Technology
              2001-2008  Tokyo Institute of Technology
All rights reserved.
For details type `(festival_warranty)'
festival> voice_rab_diphone
#<CLOSURE n (let ((me voice_rab_diphone)) (require "/usr/share/festival/voices/english/rab_diphone/festvox/rab_diphone") (if (eq me voice_rab_diphone) (error (string-append "autoload: \"" "/usr/share/festival/voices/english/rab_diphone/festvox/rab_diphone" ".scm\" does not define " (quote voice_rab_diphone)))) (apply voice_rab_diphone n))>
festival> voice_kal_diphone
#<CLOSURE nil (begin "(voice_kal_diphone)
 Set up the current voice to be male  American English (Kevin) using
 the standard diphone code." (voice_reset) (Parameter.set (quote Language) (quote americanenglish)) (require (quote radio_phones)) (Parameter.set (quote PhoneSet) (quote radio)) (PhoneSet.select (quote radio)) (set! token_to_words english_token_to_words) (require (quote pos)) (set! pos_lex_name "english_poslex") (set! pos_ngram_name (quote english_pos_ngram)) (set! pos_supported t) (set! guess_pos english_guess_pos) (lex.select "cmu") (set! postlex_rules_hooks (list postlex_apos_s_check)) (require (quote phrase)) (Parameter.set (quote Phrase_Method) (quote prob_models)) (set! phr_break_params english_phr_break_params) (require (quote tobi)) (set! int_tone_cart_tree f2b_int_tone_cart_tree) (set! int_accent_cart_tree f2b_int_accent_cart_tree) (set! postlex_vowel_reduce_cart_tree postlex_vowel_reduce_cart_data) (require (quote f2bf0lr)) (set! f0_lr_start f2b_f0_lr_start) (set! f0_lr_mid f2b_f0_lr_mid) (set! f0_lr_end f2b_f0_lr_end) (Parameter.set (quote Int_Method) Intonation_Tree) (set! int_lr_params (quote ((target_f0_mean 105) (target_f0_std 14) (model_f0_mean 170) (model_f0_std 34)))) (Parameter.set (quote Int_Target_Method) Int_Targets_LR) (require (quote kaldurtreeZ)) (set! duration_cart_tree kal_duration_cart_tree) (set! duration_ph_info kal_durs) (Parameter.set (quote Duration_Method) Duration_Tree_ZScores) (Parameter.set (quote Duration_Stretch) 1.1) (if (or kal_di_16k kal_di_8k) (begin (Parameter.set (quote Synth_Method) Diphone_Synthesize) (set! diphone_module_hooks (list kal_di_const_clusters)) (Diphone.select (quote kal))) (begin (set! UniSyn_module_hooks (list kal_diphone_const_clusters)) (set! us_abs_offset 0) (set! window_factor 1) (set! us_rel_offset 0) (set! us_gain 0.9) (Parameter.set (quote Synth_Method) (quote UniSyn)) (Parameter.set (quote us_sigpr) kal_sigpr) (us_db_select kal_db_name))) (set! after_synth_hooks (lambda (utt) (utt.wave.rescale utt 2.6))) (set! current-voice (quote kal_diphone)))>
festival> voice_us1_mbrola
#<CLOSURE n (let ((me voice_us1_mbrola)) (require "/usr/share/festival/voices/english/us1_mbrola/festvox/us1_mbrola") (if (eq me voice_us1_mbrola) (error (string-append "autoload: \"" "/usr/share/festival/voices/english/us1_mbrola/festvox/us1_mbrola" ".scm\" does not define " (quote voice_us1_mbrola)))) (apply voice_us1_mbrola n))>

```

Needles to say if the voice changed I wouldn't be typing this.

---

