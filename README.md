nabla.nvim
-----------

[![Capture.png](https://i.postimg.cc/sggrJDZR/Capture.png)](https://postimg.cc/MvNN6wDs)

This might be the next iteration for nabla.nvim. Following the issue #2, nbCloud91 brought up the idea to add a conceal layer [ref](https://github.com/KeitaNakamura/tex-conceal.vim) to hide the LaTeX Formula and only show the rendered ASCII Art. This is not possible due to the limitations of the conceals in VIM. It only allows a single character replacement which would be not enough. Not to mention the need to expand over multiple lines for multiline formulas.

A partial solution is presented here. The LaTeX formula is still concealed under a single character replacement. This lowers the level of noise when reading the document. The ASCII formula is appended inline. Furthermore, the lines which contain the ASCII art will **not** be saved with a special save override mechanism. 

To differentiate, a line which will saved and not saved, an extmark indicates that explicitely at the end of the line. 

The formulas is also very simply colored using `nvim_buf_add_highlight` which might be a nice addition, and it also indicates that the ASCII art is generated by nabla.nvim.

Requirements
------------

* Neovim nightly
* A colorscheme which supports treesitter [see here](https://github.com/rockerBOO/awesome-neovim#treesitter-supported-colorschemes)

Install
-------

Using [vim-plug](https://github.com/junegunn/vim-plug)

```vim
Plug 'jbyuki/nabla.nvim' , {'branch': 'inline'}
```

Configuration
-------------

Bind the following command:

```vim
nnoremap <F5> :lua require("nabla").place_inline()<CR>
```

Optional customizations:

```vim
let g:nabla_extmark_text = ""
let g:nabla_conceal_text = ""
let g:nabla_conceal_char = ""
```


Usage
-----

* Press <kbd>F5</kbd> on the document to first initiate **nabla.nvim**.
* Press <kbd>F5</kbd> on a LaTeX formula to generate the ASCII Formula.
