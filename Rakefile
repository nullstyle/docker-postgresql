IMAGE_NAME     = "nullstyle/postgresql"
VOLUME_CONTAINER_NAME = "pg-data"

task :build do
  system("docker build -t #{IMAGE_NAME} .")
end

task :run do
  exec("docker run -i -t --volumes-from \"#{VOLUME_CONTAINER_NAME}\" --rm -p 5432  #{IMAGE_NAME}")
end

task :bash do
  exec("docker run -i -t --volumes-from \"#{VOLUME_CONTAINER_NAME}\" --rm #{IMAGE_NAME} /bin/bash")
end

namespace :volume do
  task :make do
    system("docker run -v \"/var/lib/postgresql\" --name \"#{VOLUME_CONTAINER_NAME}\" busybox true")
  end

  task :bash do
    exec("docker run -i -t --volumes-from \"#{VOLUME_CONTAINER_NAME}\" ubuntu /bin/bash")
  end

  task :remove do
    system("docker rm --volumes=true \"#{VOLUME_CONTAINER_NAME}\"")
  end
end