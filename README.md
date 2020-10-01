# simpleTwo theme for picoCMS

## Description

**simpleTwo** is a *simple*, yet very clean, theme with two columns for [picoCMS](https://github.com/picocms/Pico) using a floating header.

A live version of the theme can be seen at [sonst-was.de](http://sonst-was.de/simpletwo/)

## Installation

### Pico, version 1.x
Copy the content of the `simpletwo` directory in the `themes` folder of your **Pico** installation and change the following setting within your `config.php`:

```php
$config['theme'] = 'simpletwo';
```

### Pico, version 2.x
Copy the content of the `simpletwo` directory in the `themes` folder of your **Pico** installation and change the following setting within your `config.yml`:

```yaml
theme: simpletwo
```

## How to use the theme

You can see, that there are four different templates included with the theme. From the visual point of view, there are all the same, but they differ in how they handle the **menu** links.

### index.twig

The `index.twig` template behaves exactly how the old *simpleTwo* theme behaved, i.e. the menu will show links to all the pages equally, no matter what the structure is. 

If, for example, the content directory looks like this:

```yaml
index.md
  section1/index.md (Introduction)
          /chapter1.md (Meeting for the first time)
          /chapter2.md (Learning about terminology)
  section2/index.md (Going deeper)
          /chapter1.md (Discovering methods)
          /chapter2.md (Adapting the methods)
```

the *menu bar* will show the content of the `Title` meta tag in the menu for all pages it can find in alphabetic order, such as:

```yaml
Going deeper
Adapting the methods
Discovering methods
Introduction
Learning about terminology
Meeting for the first time
```

As you can see, the inner structure of the content is broken, so this template is only useful for simple content where structure of the content does not
matter too much. If you plan for such a page, use this template.

### Book-like structure

For structured content that resembles a book-like structure, you can use the following three templates. Visually, they do not differ from the `index.twig` but they differ in how they handle the menu. You can invoke the use of an appropriate template by using the `Template: book` keyword in the header of the page markdown file, such as:

```yaml
Title: Learning about the terminology
Template: chapter
```

You can achieve a book-like structure, by using the correct templates for correct content.

* `book.twig` should work as a master page for your content. The menu will only show **section** items' titles, similarly what a table-of-contents would
do in a regular book. The master page should have the following meta data:

   ```yaml
   Title: The book of gardening
   Template: book
   ```

* `section.twig` should work as table of contents for chapter pages. The menu will show all **chapter** items' titles, i.e. pages that are all placed inside of that section directory. The meta data for a typical section:

   ```yaml
   Title: Introduction
   Template: section
   Toc: section
   ```

* `chapter.twig` is a template for a regular chapter. The menu will only show the links to the top of the book and to a previous page. The typical chapter meta data are:

   ```yaml
   Title: Meeting for the first time
   Template: chapter
   Toc: chapter
   ```

### More complex?

If your structure should be even more complex, then this system will not work for the deeper elements. You should probably combine it with links to those deeper sections created manually on sctructurally higher elements.

## Disclaimer
This disclaimer relates to the CSS file that I have not touched.

Please be advised, that I dont understand CSS. I really **don't**.  

So you should expect nothing from this code except that it might eat your cat, steal your wallet and do other nasty stuff. The good thing is, you can change the code yourself and tell me about it :)

