## Cek List PHP yang Terinstall di Mac
Ketikkan command dibawah ini

```.sh
brew list | grep php
```

dan akan memunculkan list php yang terinstall di Mac

```.sh
╭─goodevaninja_mac1 at Unix6fi3d in ~ using ‹ruby-2.7.6› 24-07-10 - 3:33:15
╰─○ brew list | grep php
php@7.0
php@7.1
php@7.2
php@7.3
php@7.4
php@8.0
php@8.1
php@8.2
phpmyadmin
```

## Install Multiple Changer PHP
Pertama paling cek dulu aja versinya, link source : https://medium.com/macoclock/how-to-install-multiple-php-versions-on-macos-1f290c32cd63

`brew --version`

Di laptop per 2023 versinya masih versi segini

```shell
~ ⌚ 16:08:43
$ brew --version                                                                                           ‹ruby-2.7.6›
Homebrew 4.0.9-6-gffa7ee0
Homebrew/homebrew-core (git revision 65c9173c056; last commit 2023-03-13)
Homebrew/homebrew-cask (git revision a185536932; last commit 2023-03-13)
```

Abis itu kita lakuin command `brew doctor`, lalu kita langsung install aja php multiplenya

```shell
brew tap shivammathur/php
```

Nah disini kita juga bisa nginstallin php versi sesuai yang kita mau, 

```shell
brew install shivammathur/php/php@5.6
brew install shivammathur/php/php@7.0
brew install shivammathur/php/php@7.1
brew install shivammathur/php/php@7.2
brew install shivammathur/php/php@7.3
brew install shivammathur/php/php@7.4
brew install shivammathur/php/php@8.0
```

Kebetulan saya mau coba nginstall versi 8.2 karna mau nyoba make versi laravel versi 10 yang terbaru di 2023 ini

<img width="1000" alt="Screen Shot 2023-03-21 at 16 16 28" src="https://user-images.githubusercontent.com/98740335/226562752-041c0a8b-5c7d-4b31-b5f2-f1333bbcf26b.png">

Misal kita pengen pindah dari versi PHP sekian ke sekian kita cukup lakuin command berikut

```shell
~ ⌚ 16:07:37
$ brew unlink php@8.2 && brew link --force --overwrite php@8.0                                             ‹ruby-2.7.6›
Unlinking /opt/homebrew/Cellar/php/8.2.4... 24 symlinks removed.
Linking /opt/homebrew/Cellar/php@8.0/8.0.28... 25 symlinks created.

If you need to have this software first in your PATH instead consider running:
  echo 'export PATH="/opt/homebrew/opt/php@8.0/bin:$PATH"' >> ~/.zshrc
  echo 'export PATH="/opt/homebrew/opt/php@8.0/sbin:$PATH"' >> ~/.zshrc
```

Nah setelah execute command diatas kita perlu nambahin ke file `~/.zshrc` untuk bisa diakses source dari php versi tersebut

<img width="806" alt="Screen Shot 2023-03-21 at 16 19 54" src="https://user-images.githubusercontent.com/98740335/226563519-2646733d-5c88-40c8-b0de-d41a5ae29818.png">

Intinya kalo mau pindah dari versi PHP satu ke PHP versi lain kita kudu unlink yang exist terus link ke php versi tujuan, make sure juga sudah diinstallkan, kalo belum installin aja dulu kek command diatas disesuain dengan kebutuhan versi php kita aja, berikut kita coba simulasi aja 

<img width="876" alt="Screen Shot 2023-03-21 at 16 22 09" src="https://user-images.githubusercontent.com/98740335/226564131-23456b42-ff88-44fd-bdac-69fd76b3b578.png">

Oke sudah berhasil ya.

Nah biasanya nih kalo pengen nyesuaian versi Laravelnya kita acuannya dengan versi PHP, kurang lebih gambarannya seperti berikut

<img width="584" alt="Screen Shot 2023-03-21 at 16 24 56" src="https://user-images.githubusercontent.com/98740335/226564796-1cf4fdad-c7b9-4b3b-9855-9ce524afabd3.png">

Nah ini dokumentasi Laravel ya per `21 Maret 2023` source : https://laravel.com/docs/10.x/releases

## Catatan Tambahan!
Jika kita switch ke PHP versi lain maka di `.zshrc` perlu kita command bagian source ke php versi yang tidak digunakan dan lakukan setup seperti berbikut

```shell
~ ⌚ 17:00:54
$ brew unlink php@7.3 && brew link --force php@7.3
```

Simpan perubahan dan tutup ulang terminal lalu lakukan cek `php --version`
