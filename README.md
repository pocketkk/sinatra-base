# sinatra-base
Base for Sinatra Apps to be deployed to Heroku using Postgresql

Create a migration for dynamic data

    rake db:create_migration NAME=create_posts

Edit the migration with the appropriate fields (Example)

	def self.up
		create_table :posts do |t|
			t.string :title
			t.text :body
			t.timestamps
		end
	end
	def self.down
		drop_table :posts
	end

Run the migration

	rake db:migrate

Use tux to add data if needed to database

	$ tux
	>> Post.create(title: 'Testing the title', body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum venenatis eros eget lectus hendrerit, sed mattis quam pretium. Aenean accumsan eget leo non cursus. Aliquam sagittis luctus mi, quis suscipit neque venenatis et. Pellentesque vitae elementum diam. Quisque iaculis eget neque mattis fermentum. Donec et luctus eros. Suspendisse egestas pharetra elit vel bibendum.')
	>>
	>> Post.all
	D, [2013-06-08T12:26:44.929333 #42914] DEBUG -- :   Post Load (0.2ms)  SELECT "posts".* FROM "posts"
	=> [#<Post id: 1, title: "Testing the title", body: "Lorem ip

Initialize Git Repository

	git init
	git add .
	git commit -m 'initial commit'

Deploy to Heroku

	heroku create <name-of-app>
	git push heroku master
	heroku rake db:migrate

Reminders:

* Use <%=h to display html safe

Almost completely pulled from:  http://mherman.org/blog/2013/06/08/designing-with-class-sinatra-plus-postgresql-plus-heroku/#.VaxKdRNVikp