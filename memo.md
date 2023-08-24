# メモ集

## 環境セットアップ
[Spring Security および Angular チュートリアル](https://spring.pleiades.io/guides/tutorials/spring-security-and-angular-js/)にしたがって実行

途中[Creating a New Application with Spring Boot and Angular](https://github.com/dsyer/spring-boot-angular)の指示にも従った

### "Fatal error compiling: error: release version 17 not supported"のエラーが発生
新規springプロジェクト作成後、`./mvnw install`を実行すると"Fatal error compiling: error: release version 17 not supported"のエラーが発生した

単にインストールされているJavaのバージョンが低いだけなので、 Java17以降のJDKをインストールする

### "Error: You need to specify a command before moving on. Use '--help' to view the available commands."のエラーが発生
Angular CLIのインストールが正しく行われたか確認しようと、`./ng --version`を実行すると、"Error: You need to specify a command before moving on. Use '--help' to view the available commands."のエラーが発生した

資料に書かれているAngularのバージョンは古く、現在のバージョンのAngularは`--`が要らない。よって`./ng version`と実行すればよい

### npmのテストが終わらないため、アプリケーションが起動しない
`mvn spring-boot:run`コマンドを実行しても、npmのテスト時にChromeを裏で起動させてテストを行っているが、そのChromeのバイナリを設定していないため、テストを実行できず、その後のmavenフェーズに進まない

そこで今のところは`mvn spring-boot:run -DskipTests`と`-DskipTests`オプションをつけて実行させて、 npmのテストを省略して実行させる