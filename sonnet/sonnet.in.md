# Spellchecking made easy

Sonnet is a useful framework provided by KDE for software developers who
want to solve the problem of spellchecking in text editors. It has a plugin
based architechture with support for HSpell, Enchant, ASpell and HUNSPELL
plugins. It even supports automated language detection, based on a combination of different algorithms.

## Spellchecking in your QTextEdit

Sonnet can be easily integrated into your QTextEdit as follows:

//@@snippet(sonnet/examples/textedit.cpp, simple_textedit_example, cpp)

Sonnet::SpellCheckDecorator can also be extended in various ways to spell check text
that is formatted differently, for example in emails.

//@@snippet(sonnet/examples/textedit.cpp, simple_email_example, cpp)

So, you can use MailSpellCheckDecorator in exactly the same way as you would use SpellCheckDecorator,
but with the added functionality that MailSpellCheckDecorator will ignore quoted parts of a email.

## Language Detection in Sonnet

Sonnet can determine the difference between ~75 languages for a given string.
It is based off a perl script origionaly written by Maciej Ceglowski called Languid. His script used a two-part heuristic to determine language. First the text is checked for the scripts it contains, next for each set of languages using those scripts a n-gram frequency model of a given language is compared to a model of the text. The most similar language model is assumed to be the language. If no language is found an empty string is returned.

Here you see a simple example of language detection using the GuessLanguage class from Sonnet:

~~~ {.cpp}
    GuessLanguage languageGuesser;
    QString lang = languageGuesser.identify("My awesome text");
~~~

## GUI Widgets provided by Sonnet

Sonnet also provides some GUI widgets that can be used by Qt applications to configure settings in Sonnet; for example Qt applications can use the DictionaryComboBox class from Sonnet to get a QComboBox that can configure the dictionary used by Sonnet.

//@@snippet(sonnet/examples/dialogexample.cpp, dictionary_combo_box_example, cpp)

The ConfigDialog class from Sonnet provides a more advanced configuration dialog to configure settings such as whitelisting words, skipping run-together words as well as enabling or disabling auto detection of the language.