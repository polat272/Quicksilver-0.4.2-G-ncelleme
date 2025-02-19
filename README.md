## Quicksilver-0.4.2-Güncelleme

Güncelleme bloğuna geldiyseniz sırasıyla yapabilirsiniz arkadaşlar. Şunu unutmayalım, ilgili blok gelmeden önce yani aceleyle güncellemeyi yapmak kesinlikle size bir artı sağlamaz aksine hata alırsınız. Acele etmemenizi tavsiye ediyorum.

Blok, 212.000 olmadan yapmayın kesinlikle.

Güncelleme yapmak için log kaydında "ERR UPGRADE "upgrade-v0.4.2" NEEDED at height: 212000" uyarısını görmelisiniz.

Log kaydına bakmak için;
```
journalctl -u quicksilverd -f -o cat
```

Güncelleme Komutları

```
1) sudo systemctl stop quicksilverd
2) sudo su
3) cd
4) rm -rf quicksilver 
5) git clone https://github.com/ingenuity-build/quicksilver.git
6) cd quicksilver
7) git checkout v0.4.2
8) make build
9) sudo chmod +x ./build/quicksilverd && sudo mv ./build/quicksilverd /usr/local/bin/quicksilverd
10) sudo systemctl restart quicksilverd
```

Güncellemeyi yaptıktan sonra teyit etmek için;

```
quicksilverd version
```
Yazdıktan sonra gelen çıktı 0.4.2'yse tamamdır.

## Güncellemeyi yaparken "error 127" hatası alanlar ya da go kurulu değil hatası alanlar için
```
1-cd $HOME
2-wget -O go1.18.2.linux-amd64.tar.gz https://go.dev/dl/go1.18.2.linux-amd64.tar.gz
3-rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.2.linux-amd64.tar.gz && rm go1.18.2.linux-amd64.tar.gz
4-echo 'export GOROOT=/usr/local/go' >> $HOME/.bashrc
5-echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
6-echo 'export GO111MODULE=on' >> $HOME/.bashrc
7-echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bashrc && . $HOME/.bashrc
8-go version
```

Bu kodları girdikten sonra yeniden güncelleme komutlarından şunlarla devam ediyoruz;

```
1) cd quicksilver
2) git checkout v0.4.2
3) make build
4) sudo chmod +x ./build/quicksilverd && sudo mv ./build/quicksilverd /usr/local/bin/quicksilverd
5) sudo systemctl restart quicksilverd
```
## Exit Code hatası alanlar bu komutları kullansın

```
1) rm -rf /usr/local/bin/quicksilverd
2) sudo systemctl stop quicksilverd
3) cd quicksilver
4) git pull
5) git checkout v0.4.2
6) make install
7) sudo systemctl start quicksilverd
```

Hepinize kolay gelsin.
